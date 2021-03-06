!SLIDE 
#8) Caracteristica: Habilitar Votos en Tópicos 

!SLIDE commandline incremental
### Siguiendo el Desarrollo Basado en Pruebas
	rake cucumber FEATURE=features/3_votos.feature

!SLIDE
	language: es
	Característica: Votos
		Para determinar que discurso dar
		Los usuarios deben votar por sus favoritos topicos.

		Escenario: Viendo los votos
	    	Cuando visito la página topicos
	    	Entonces deberia ver  "0 votos"

!SLIDE
	Por el mensaje de error notaras que nos hace falta "votos"
	Y ademas tenemos que modificar la vista.

!SLIDE bullets incremental transition=fade
# Votos
* Cada voto sera un objeto (tendra una fila en la base de datos)
* Cuando alguien vote en un tópico, crearemos un nuevo objeto "voto" y lo guardaremos
* Cada voto es asociado con un específico tópico.

!SLIDE subsection
# Asociaciones en Rails

!SLIDE  title-slide center  bullets incremental
![has_many](/images/asociaciones_en_mafalda.png)


!SLIDE commandline incremental 
### Agregar votos: Necesitamos un modelo y un controlador

	rails generate resource voto topico_id:integer 

!SLIDE commandline incremental 
### Creamos la tabla votos en la BD, a través del migrate

	rake db:migrate

!SLIDE
# Topico has_many :votos
# Voto belongs_to :topicos

!SLIDE   
# Agregar las asociaciones

	@@@ruby
	../app/models/topico.rb
	class Topico < ActiveRecord::Base
	  has_many :votos
	end

	../app/models/voto.rb

	class Voto < ActiveRecord::Base
	   belongs_to :topico
	end

<!-- !SLIDE  title-slide center  bullets incremental
![has_many](/images/asociaciones_rails.png) -->

!SLIDE command 
#Para entender mejor juega en la consola
	$rails c

	ruby-1.9.2-head :001 > t = Topico.new(:titulo => "Mi Topico")
	 => #<Topico id: nil, titulo: "Mi Topico", descripcion: nil, created_at: nil, updated_at: nil> 
	ruby-1.9.2-head :002 > t.votos
	=> []
	ruby-1.9.2-head :004 > t.votos.build
	 => #<Voto id: nil, topico_id: nil, created_at: nil, updated_at: nil> 
	ruby-1.9.2-head :005 > t.votos
	 => [#<Voto id: nil, topico_id: nil, created_at: nil, updated_at: nil>] 
	ruby-1.9.2-head :006 > t.save
	 => true 
	ruby-1.9.2-head :007 > t.votos
	 => [#<Voto id: 5, topico_id: 4, created_at: "2011-05-04 11:24:47", updated_at: "2011-05-04 11:24:47">] 

!SLIDE subsection
#Hagamos pasar la prueba! 

!SLIDE  
## Primero indiquemos la cantidad de votos 
	Utiliza el helper pluralize para agregar la cantidad de votos a tu vista
	<%= pluralize(topico.votos.length, "voto") %>

<!SLIDE bullets >
## Luego un acceso para que los usuarios voten
* Con "rake routes | grep votos" explora las URLs de votos 
* Luego edita "/app/views/topicos/index.html.erb" y agrega el siguiente helper method:

<pre style="font-size:22px; color:black; margin-left:100px; color:red;">	
	&#60;%= link_to '+1', votos_path(:topico_id => topico.id), 
	:method => :post %&#62;
</pre>

* Observa el argumento :metodo => :post

!SLIDE
## Por último, tenemos que agregar la misma lógica que probamos en la consola 
### Fijate de nuevo en las rutas de votos.

<!SLIDE code >
    $ rake routes | grep votos
<div >
    votos GET    /votos(.:format)            {:action=>"index", :controller=>"votos"}
	      POST   /votos(.:format)            {:action=>"create", :controller=>"votos"}
	.........

	<span>
	Fijate en la segundo expresión de "votos/"
	Nos está indicando que el verbo "POST" corresponde a la acción "create" del controlador "votos"
	</span
</div>
	
!SLIDE
## Abre el controller topicos y agrega el siguiente código	
!SLIDE

	@@@ruby
	class VotosController < ApplicationController
	   def create
	    topico = Topico.find(params[:topico_id])
	    voto   = topico.votos.build

	    if voto.save
	      flash[:notice] = 'El voto fue creado.'
	    else
	      flash[:error] = 'Lo siento. No pudimos contar su voto.'
	    end
	    redirect_to(topicos_path)
	  end
	 end
	
!SLIDE subsection
#Volvamos a la prueba ... 

!SLIDE
### Esta vez ejecuta el suite completo.
<pre style="font-size:1.7em; margin-left:0">	
	$ rake cucumber
	/Users/carmen/.rvm/rubies/ruby-1.9.2-p180/bin/ruby -S bundle exec cucumber  --profile default
	Using the default profile...
	# language: es
	Característica: Topicos
<div style="color:green; margin:0; padding:0">
	  Para ver una lista potencial de topicos
	  Los usuario deben crear y editar los mismos
</div>
	  Escenario: Nuevo Topico               # features/1_topicos.feature:6
<div style="color:green; margin:0; padding:0">
	    Cuando visito topicos               # features/step_definitions/web_steps_es.rb:29
	    Y hago click en "New Topico"        # features/step_definitions/web_steps_es.rb:33
	    Entonces debo ver el botón "Create" # features/step_definitions/topico_steps.rb:6
</div>
	.......
</pre>
<pre style="color:green">
6 scenarios (6 passed)
23 steps (23 passed)
0m1.217s
</pre>
!SLIDE
# Veras que todas las pruebas han pasado!!!


!SLIDE commandline incremental
## Checkpoint!!!! Commit frecuentemente y deploy 	
	git add .
	git commit -m "Votos habilitados"
	......
	git push heroku master
	...
	
!SLIDE 
# Chequea tu nueva aplicación RoR
### http://<tu_nombre_generado>.heroku.com/	
	