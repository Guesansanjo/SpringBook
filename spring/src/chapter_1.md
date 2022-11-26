# Chapter 1 : API simple

---
Spring Boot Tutorial

---


#### Spring Boot 

API recibe `GET` `POST` `PUT` `DELETE`

Ejemplo creacion de modelo/entidad para crear API : 

Creamos StundentEntity

```java
public class StundentEntity{

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
