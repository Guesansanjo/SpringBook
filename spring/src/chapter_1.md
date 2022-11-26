# Chapter 1 : API simple

---
Spring Boot Tutorial

---


#### Spring Boot 

API recibe `GET` `POST` `PUT` `DELETE`

Ejemplo creacion de modelo/entidad para crear API : 

    Creamos StundentEntity

```java
//Primera hibernate la segunda para la base de datos
@Entity
@Table
public class StundentEntity{

    @Id
    @SequenceGenerator(
        name = "student_sequence",
        sequenceName = "student_sequence",
        allocationSize = 1
    )
    @GeneratedValue(
        strategy = GenerationType.SEQUENCE,
        generator = "student_sequence"
    )
    private Long id;
    private String name;
    private String email;
    private Localdate dateOfBirth;
    private Integer age;

    //Creamos 3 Constructores ...

    public StudentEntity(){

    }

     public StudentEntity(Long id,String name,String email,Localdate dateOfBirth,Integer age){
        this.id = id;
        this.name = name;
        this.email = email;
        this.dateOfBirth = dateOfBirth;
        this.age = age;
    }
    //Uno sin id porque la base de datos lo autogenera con autoadd en SQL
     public StudentEntity(String name,String email,Localdate dateOfBirth,Integer age){
        this.name = name;
        this.email = email;
        this.dateOfBirth = dateOfBirth;
        this.age = age;
    }
    //Generamos Getters y Setters ademas un ToString y tenemos StudentEntity ...
}

```

    Creamos StundentController

```java
//Anotaciones spring controller y endpoint
@RestController
@RequestMapping(path = "api/v1/student")
public class StudentController{

    private final StudentService studentService ;   

    //Tenemos que instanciasr StudentService con autowired , y asi instanciado e inyectado tiene que ser una spring bean con @Service

    @Autowired
    public StudentController(StudentService studentservice){
        this.studentService = studentService;
    }
    //localhost/8080/api/v1/student 
    //Mostrara el codigo siguiente
    @GetMapping
    public List<StudentEntity> getStudent(){
   
    };

}
```

Para poder llamarlo y que se comunique con la base de datos creamos StudentService

```java

@Service
public class StudentService{

    
    private final StudentRepository studentRepository;

    @Autowired
    public StudentService (StudentRepository studentRepository ){
        this.studentRepository = studentRepository;
    }

    @GetMapping
    public List<StudentEntity> getStudent(){
        return studentRepository.findAll();
    //findAll lo saca de JpaRepository ...
    }
}

```

Por ultimo creamos el StudentRepository

```java
//Long porque el id es Long esta es la DATA ACCES LAYER que usaremos dentro de el Service que es la logica

@Repository
public interface StudentRepository extends JpaRepository <StudentEntity,Long>{

}

```