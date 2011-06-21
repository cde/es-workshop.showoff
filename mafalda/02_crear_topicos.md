!SLIDE bullets incremental transition=fade
#2) Observemos los requerimientos o características deseadas

* Tipicamente utilizaras el framework de pruebas de tu preferencia para escribir los requerimientos
* ( Rspec, TestUnit, Cucumber o una combinación de ellas).
* En el workshop estamos utilizado "cucumber".

!SLIDE bullets incremental transition=fade
# Observa las pruebas que hemos escritos de antemano para ganar tiempo
        $  ls -la features/

!SLIDE subsection
# Desarrollo basado en Pruebas

!SLIDE bullets incremental transition=fade
* Basado en el requerimiento, primero escribimos la prueba
* Ver fallar la prueba
* Luego escribimos el código (implementación)
* Vemos pasar la prueba

<!SLIDE transition=fade>
#Escribamos la prueba usando cucumber.

    #language: es
    Característica: Topicos
        Para ver una lista potencial de topicos
        Los usuario deben crear y editar los mismos

        Escenario: Nuevo Topico
            Cuando visito la página topicos
            Y hago click en "New Topico"
            Entonces debo ver el botón "Create"



!SLIDE bullets incremental transition=fade
# 3) Primera característica: Agregar Topicos
* que queremos decir con "agregar tópicos?"
* rails "scaffolding" para generar paginas y codigo
* creando la Base de datos con una nueva tabla (migration)
* repasar los pasos.


!SLIDE
# Observemos fallar la prueba

    @@@ ruby
    $ rake cucumber FEATURE=features/1_topicos.feature

!SLIDE
# Los escenarios en cucumber son pruebas & documentación a la vez.


!SLIDE
#Hagamos pasar la prueba
#Que necesitamos?

!SLIDE subsection
# Tópicos

!SLIDE bullets incremental transition=fade
# Tópicos
* El tópico va a estar compuesto de título y descripción
* Tendremos acciones de CRUD. (Acronimo de Crear, Obtener, Actualizar y Borrar por sus siglas en inglés)

* Create: crear un nuevo tópico
* Read: Leer tópicos
* Update: Modificar los tópicos
* Delete: Borrar los tópicos del sistema


!SLIDE
# Implementando  MVC con scaffold
    @@@ ruby
    $ rails generate scaffold topico titulo:string descripcion:text
    $ rake db:migrate

!SLIDE
#  Ver pasar la prueba
    @@@ ruby
    $ rake cucumber FEATURE=features/1_topicos.feature

!SLIDE commandline
    @@@ ruby
    $ rails server
    http://localhost:3000/topicos

!SLIDE incremental
#Que acabamos de hacer?
    El Modelo
        create db/migrate/20110503202056_create_topicos.rb
        create app/models/topico.rb

    Las Vistas necesarias incluyendo el subdirectorio por el modelo tópico.

        create app/views/topicos
        create app/views/topicos/index.html.erb
        create app/views/topicos/edit.html.erb
        create app/views/topicos/show.html.erb
        create app/views/topicos/new.html.erb
        create app/views/topicos/_form.html.erb

    El Controlador
        create app/controllers/topicos_controller.rb
    Rutas
        config/routes.rb
            Mafalda::Application.routes.draw do
                resources :topicos

!SLIDE  title-slide center
![Architectura](../public/images/mvc_es.png)

<!SLIDE >
# Modelo-Vista-Controlador
    Modelo
        * representa lo que existe en la base de datos
        * ActiveRecord
    Vista
        * el modelo generado como HTML
        * ActionView, erb
    Controlador
        * recibe acciones HTTP (GET, POST, PUT, DELETE)
        * decide que hacer, típicamente desplegar la vista
        * ActionController


!SLIDE commandline code

#4) Mi sitio a la vista de todos
$ git init


$ git add .
$ git commit -m "Aplicación web básica, incluyendo el modelo topico"
$ git push origin master

<a href = "http://www.wiki.devchix.com/index.php?title=User_talk:Carmen#Puesta_a_la_Vista_del_Mundo">Explicaciones / Instrucciones</a>


!SLIDE
# Commit en una fase temprana & pon a producción "frecuentemente”


!SLIDE commandline
    carmen(mafalda)(master)$heroku create mi-mafalda
        Creating mi-mafalda... done, stack is bamboo-mri-1.9.2
        http://mi-mafalda.heroku.com/ | git@heroku.com:mi-mafalda.git
        Git remote heroku added

!SLIDE commandline code

$ git push heroku master
$ heroku rake db:migrate


!SLIDE   bullets incremental
# Repite los pasos del Desarrollo basado en Pruebas:
* Escribir y/o ejecutar prueba
* Ver fallar la prueba.
* Implementar la solución y ver pasar la prueba

*  Observa con detalle las pruebas restantes pruebas en el directorio /features 



          [remote "origin"]
                  fetch = +refs/heads/*:refs/remotes/origin/*
                  url = https://github.com/schacon/showoff.git


