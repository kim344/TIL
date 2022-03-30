> Room 설명

* Room은 기존의 안드로이드에서 제공하는 DB인 SQLite를 활용하면서 쉽고, 간결하고, 안정성 있게 사용할 수 있도록 하는 라이브러리입니다.

  자세한 설명은 [안드로이드 Room](https://developer.android.com/training/data-storage/room) 참조


> Room 구성요소

* **Database** - 데이터베이스의 전체 소유자 역할, **DB 생성 및 버전관리**
* **Entity** - 데이터베이스의 **테이블** (DB에 저장될 데이터 형식)
* **DAO** - 데이터베이스에 접근하여 수행할 작업(**SELECT, UPDATE, DELETE**)을 인터페이스로 정의

![](https://images.velog.io/images/kim344/post/022f7639-5cdb-4991-978d-03aa65716732/image.png)

> Room 사용법
Android Studio 4.2.2

### build.gradle(Module) 설정
```
plugins {
    // Room Setting
    id 'kotlin-kapt'
}

dependencies {
    // Room Setting
	def room_version = "2.4.1"

    implementation("androidx.room:room-runtime:$roomVersion")
    kapt("androidx.room:room-compiler:$roomVersion")
}
```

### Entity 생성

@Entity : 테이블로 사용할 data class Entity 선언
@PrimaryKey : 테이블의 각 행을 고유하게 식별하는 기본 키
@ColumnInfo : 컬럼명 지정

```
// TableName & ColumnName 미지정
@Entity
data class Inform(
    var name: String,
    var gender: String,
    var phoneNumber: String
){
    @PrimaryKey(autoGenerate = true)
    var id = 0
}

// TableName & ColumnName 지정
@Entity(tableName = "InformTable")
data class Inform(
    @ColumnInfo(name = "inform_name")
    var name: String,
    
    @ColumnInfo(name = "inform_gender")
    var gender: String,
    
    @ColumnInfo(name = "inform_number")
    var phoneNumber: String
){
    @PrimaryKey(autoGenerate = true)
    var id = 0
}
```
 - **TableName & ColumnName 미지정**
    => TableName = Inform
	=> ColumnName = name, gender, phoneNumber
    <br>    
 - **TableName & ColumnName 지정**
    => TableName = InformTable
	=> ColumnName = inform_name, inform_gender, inform_number
	<br><br>

### DAO 생성
```
@Dao
interface InformDao {

    @Insert
    fun insert(inform: Inform)

    @Update
    fun update(inform: Inform)

    @Delete
    fun delete(inform: Inform)

    @Query("SELECT * FROM Inform")
    fun selectAll(): List<Inform>

    @Query("DELETE FROM Inform ")
    fun deleteAll()

    @Query("SELECT * FROM Inform WHERE name = :name")
    fun selectByName(name: String)
    
}
```
 - **TableName & ColumnName 미지정**
 ```
 @Query("SELECT * FROM Inform WHERE name = :name")
 fun selectByName(name: String)
 ```
 - **TableName & ColumnName 지정**
 ```
 @Query("SELECT * FROM InformTable WHERE inform_name = :name")
 fun selectByName(name: String)
 ```
<br><br>

### Database 생성
@Database : 해당 class가 Database임을 알려주는 어노테이션

```
@Database(entities = [Inform::class], version = 1)
abstract class InformDatabase : RoomDatabase() {
    abstract fun informDao(): InformDao

    companion object {
        private var instance: InformDatabase? = null

        @Synchronized
        fun getInstance(context: Context): InformDatabase? {
            if (instance == null) {
                synchronized(InformDatabase::class) {
                    instance = Room.databaseBuilder(
                        context.applicationContext,
                        InformDatabase::class.java,
                        "inform-db"
                    )
                        // MainThread 에서 사용하면 에러남
                        // 강제로 Main Thread 에서 사용할게 명시
                        .allowMainThreadQueries()
                        .build()
                }
            }
            return instance
        }
    }

}
```
**리소스를 많이 사용하기 때문에 싱글톤 사용을 권장함!!**
![](https://images.velog.io/images/kim344/post/3dd78a1e-e6b5-4fc6-9f62-69f9fb9369d2/image.png)

### 참고자료
[Android DB Room이란?](https://velog.io/@ryalya/Android-DB-Room%EC%9D%B4%EB%9E%80)<br>
[안드로이드 Room의 사용법과 예제](https://todaycode.tistory.com/39)<br>
[Room 활용하여 데이터 저장하기](https://hanyeop.tistory.com/193)
