!SLIDE bullets incremental transition=fade
#2) Observemos los requerimientos o características deseadas

* Tipicamente utilizaras el framework de pruebas de tu preferencia para escribir los requerimientos
* ( Rspec, TestUnit, Cucumber o una combinación de ellas).
* En el workshop estamos utilizado "Cucumber".

!SLIDE commandline incremental transition=fade
# Observa las pruebas que hemos escritos de antemano para ganar tiempo
	ls -la features/

!SLIDE subsection
# Desarrollo basado en Pruebas

!SLIDE bullets incremental transition=fade
* Basado en el requerimiento, primero escribimos la prueba
* La vemos fallar
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
# 3) Primera característica: Topicos
* que queremos decir con "agregar tópicos?"
* rails "scaffolding" para generar las plantillas y codigos
* creando la Base de datos con una nueva tabla (migration)
* repasar los pasos.


!SLIDE commandline incremental 
# Observemos fallar la prueba

	rake cucumber FEATURE=features/1_topicos.feature

!SLIDE transition=fade
# Los escenarios en cucumber son pruebas & documentación a la vez.


!SLIDE transition=fade
#Hagamos pasar la prueba
#Que necesitamos?

!SLIDE subsection 
# Tópicos

!SLIDE  title-slide center transition=fade
![TOPICO](/images/topico.png)

!SLIDE bullets incremental transition=fade
# Tópicos
* El tópico va a estar compuesto de título y descripción
* Tendremos acciones de CRUD. (Acrónimo de Crear, Obtener, Actualizar y Borrar por sus siglas en inglés)

* Create: crear un nuevo tópico
* Read: Leer tópicos
* Update: Modificar los tópicos
* Delete: Borrar los tópicos del sistema


!SLIDE commandline incremental transition=fade
# Implementando  MVC con scaffold
  
	rails generate scaffold topico titulo:string descripcion:text
	
	rake db:migrate

!SLIDE commandline incremental transition=fade
#  Ver pasar la prueba
	rake cucumber FEATURE=features/1_topicos.feature

!SLIDE commandline incremental
    rails server
    http://localhost:3000/topicos

!SLIDE incremental transition=fade
#Que acabamos de hacer?
    El Modelo
        create db/migrate/20110503202056_create_topicos.rb
        create app/models/topico.rb

    Las Vistas necesarias incluyendo el subdirectorio por 
	el modelo tópico.

        create app/views/topicos
        create app/views/topicos/index.html.erb
        create app/views/topicos/edit.html.erb
        create app/views/topicos/show.html.erb
        create app/views/topicos/new.html.erb
        create app/views/topicos/_form.html.erb
!SLIDE incremental transition=fade
#...Que acabamos de hacer? (cont)
    El Controlador
        create app/controllers/topicos_controller.rb
    
	Rutas
        config/routes.rb
            Mafalda::Application.routes.draw do
                resources :topicos

!SLIDE  title-slide center transition=fade
![Architectura](/images/mvc_es.png)

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


<!SLIDE bullets transition=fade>
#4) Mi sitio a la vista de todos
* Commit tus cambios en tu repositorio local y remoto
* Deploy en Heroku

<div style="margin-left:20px;">
<a href = "http://www.wiki.devchix.com/index.php?title=User_talk:Carmen#Puesta_a_la_Vista_del_Mundo" target="_blank">Explicaciones / Instrucciones</a>
</div>

!SLIDE commandline incremental transition=fade
	git init
	....
	git add .
	git commit -m "Aplicación web básica, incluyendo el modelo topico"


!SLIDE transition=fade
# Commit en una fase temprana & frecuentemente 


<!SLIDE image center transition=fade>
# Pon a producción "regularmente”
<img src="/images/proceso_desarrollo.png" >

!SLIDE commandline
    carmen(mafalda)(master)$heroku create 
        Creating afternoon-water-081... done, stack is bamboo-mri-1.9.2
        http://afternoon-water-081.heroku.com/ | git@heroku.com:afternoon-water-081.git
        Git remote heroku added

	Nota: afternoon-water-081 es el nombre creado por heroku, 
	distinto x cada usuario  

!SLIDE commandline incremental

    $ git push heroku master
    $ heroku rake db:migrate


!SLIDE   bullets incremental transition=fade
# 5) Rutas / Mapeos
* REST las URLs representan recursos y no acciones
* "Tópico" es un recurso


<!SLIDE code >
    $ rake routes
<div >
    topicos GET    /topicos(.:format)          {:action=>"index", :controller=>"topicos"}
            POST   /topicos(.:format)          {:action=>"create", :controller=>"topicos"}
 new_topico GET    /topicos/new(.:format)      {:action=>"new", :controller=>"topicos"}
edit_topico GET    /topicos/:id/edit(.:format) {:action=>"edit", :controller=>"topicos"}
     topico GET    /topicos/:id(.:format)      {:action=>"show", :controller=>"topicos"}
            PUT    /topicos/:id(.:format)      {:action=>"update", :controller=>"topicos"}
            DELETE /topicos/:id(.:format)      {:action=>"destroy", :controller=>"topicos"}
</div>

!SLIDE commandline transition=fade
    $rails console
    Loading development environment (Rails 3.0.5)
    ruby-1.9.2-head :001 > app.topicos_path
    => "/topicos"
    ruby-1.9.2-head :002 > app.topicos_url
     => "http://www.example.com/topicos"
    ruby-1.9.2-head :003 >

!SLIDE
#Re-mapeo

	Mafalda::Application.routes.draw do
	   resources :topicos
	   ...
	   root :to => 'topicos#index'
	 end


	$ git rm public/index.html

!SLIDE  bullets incremental transition=fade
# Repite los pasos del Desarrollo basado en Pruebas:
* Escribir y/o ejecutar prueba
* Ver fallar la prueba.
* Implementar la solución y ver pasar la prueba
* Observa con detalle las pruebas restantes pruebas en el directorio /features

!SLIDE  bullets incremental transition=fade
# 6) Escenario: Creando un tópico
	* Ejecutemos el segundo escenario.
	* Observa el fallo.

!SLIDE  commandline incremental
	$rake cucumber FEATURE=features/1_topicos.feature:11:18

!SLIDE transition=fade
	Escenario: Creando un topico
   		Cuando visito topicos
		Y hago click en "New Topico"
		Cuando completo el campo "Titulo" con "Rails Fixtures"
		Y completo el campo "Descripcion" con "Rails es genial"
		Y oprimo "Create"
		Entonces debo ver "Rails Fixtures"
		Y debo estar en inicio
		

<!SLIDE bullets incremental transition=fade>

* Abre app/controllers/topicos_controller.rb
* Fíjate en las acciones new y create.
* En la acción create hay un re-ruteo a un único tópico:
format.html { redirect_to(@topic) } 

!SLIDE 	
	Deseamos que el re-ruteo sea a la pagina de inicio 
	(lista de topicos)

!SLIDE
	Escenario: Creando un topico
   		Cuando visito topicos
		Y hago click en "New Topico"
		Cuando completo el campo "Titulo" con "Rails Fixtures"
		Y completo el campo "Descripcion" con "Rails es genial"
		Y oprimo "Create"
		Entonces debo ver "Rails Fixtures"
<pre style="color:red">		
	Y debo estar en inicio
</pre>	
!SLIDE
	Redirecciona la ruta
		format.html { redirect_to(root_path) }
	
!SLIDE 
	Corre de vuelta la prueba
	
	$rake cucumber FEATURE=features/1_topicos.feature

	
<pre style="color:green">
Genial!
2 scenarios (2 passed)
10 steps (10 passed)
</pre>	

!SLIDE  transition=fade
# 7) Característica: Topicos y Detalles

	* Ejecutemos el segundo feature.
	* Observa el fallo y determina cual es el requerimiento.

	$rake cucumber FEATURE=features/2_topicos_y_detalles.feature
	

!SLIDE  bullets incremental transition=fade
# Helpers
* Conjunto de métodos para establecer vínculos y obtener las direcciones URL (a href tags) 

* Rails proporciona una variedad de metodos que pueden ser utilizados en las Vistas
* Son llamados helpers - ActionView::Helpers
  
  
!SLIDE   bullets incremental transition=fade
* Utiliza el método "link_to"
* En app/views/topics/index.html.erb determina los cambios para hacer pasar tus pruebas 

!SLIDE commandline incremental
## Checkpoint!!!! Commit frecuentemente 	
	git add .
	git commit -m "Titulos son links"
	