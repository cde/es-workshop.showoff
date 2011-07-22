!SLIDE 
#8) Caracteristica: Habilitar Votos en Tópicos 

!SLIDE
Siguiendo el Desarrollo Basado en Pruebas

	$ rake cucumber FEATURE=features/3_votos.feature

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

!SLIDE transition=fade
# Votos
* Cada voto sera un objeto (tendra una fila en la base de datos)
* Cuando alguien vote en un tópico, crearemos un nuevo objeto "voto" y lo guardaremos
* Cada voto es asociado con un específico tópico.

!SLIDE subsection
# Asociaciones en Rails

!SLIDE  title-slide center  bullets incremental
![has_many](/images/asociaciones_rails.png)

# Topico has_many :votos
# Voto belongs_to :topicos

!SLIDE 
# Agregar votos

Necesitamos un modelo y un controlador

	$ rails generate resource voto topico_id:integer
	$ rake db:migrate

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

!SLIDE  title-slide center  bullets incremental
![has_many](/images/asociaciones_rails.png)

!SLIDE command
#Juega en la consola
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
#Volvamos a la prueba 

!SLIDE 
	language: es
	Característica: Votos
		Para determinar que discurso dar
		Los usuarios deben votar por sus favoritos topicos.

		Escenario: Viendo los votos
	    	Cuando visito la página topicos
	    	Entonces deberia ver  "0 votos"

!SLIDE
Ejecuta de nuevo la prueba y te encontraras con otro tipo de error. 

	$ rake cucumber FEATURE=features/3_votos.feature

!SLIDE
Utiliza el helper pluralize para agregar la cantidad de votos a tu vista
	
<%= pluralize(topico.votos.length, "voto") %>

<!SLIDE >
#Permitir que los usuarios voten
* Con rake routes a explora las URLs de votos 
* Luego edita /app/views/topicos/index.html.erb y agrega el siguiente helper method:

<div style="font-size:22px; color:black; margin-left:100px; color:red;">	
	&#60;%= link_to '+1', votos_path(:topico_id => topico.id), :method => :post %&#62;
</div>
* Y Crea la accion en el Controlador  	

!SLIDE

	@@@ruby
	class VotosController < ApplicationController
	   def create
	    topico = Topico.find(params[:topico_id])
	    voto   = topico.votos.build

	    if voto.save
	      flash[:notice] = 'El voto fue creado.'
	    else
	      flash[:notice] = 'Lo siento. No pudimos contar su voto.'
	    end
	    redirect_to(topicos_path)
	  end
	 end
	
!SLIDE subsection
#Volvamos a la prueba ... 

!SLIDE
Esta vez ejecuta el suite completo.
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
Veras que todas las pruebas han pasado!!!


