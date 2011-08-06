!SLIDE subsection
# Crear una Aplicación RoR Web

<!SLIDE bullets transition=fade>
## El Proyecto de Hoy
<div style="width:100%; height:150px; line-height:2;">
	<div style="float:left; width:20%;">
		<img src="/images/mafalda.jpg"/>
	</div>
	<div style="float:right;  width:80%; font-size:20px;">
		<p>Mafalda es una niña preocupada por la humanidad y la paz mundial 
		<br/>
		A Mafalda le gusta hablar de la vida y tiene muchos tópicos que compartir!!!
		</p>
		<p>
		Nuestra misión es ayudar a Mafalda con una "app Web" donde ella pueda  agregar tópicos y sus amigos puedan votar en ellos. </p>
	</div>
</div>

!SLIDE bullets incremental transition=fade
# Nuestra aplicación web va a:
* Crear, editar y/o eliminar tópicos
* Tener la habilidad de votar los tópicos.
<!SLIDE title-slide center>
<img src="/images/mafalda_app.png">


!SLIDE bullets incremental transition=fade
#También vamos a explorar otros conceptos!
* Desarrollo basado en pruebas (TDD - Test Driven Development)
* Git
* Heroku
* Bundle (manejador de gemas)

!SLIDE subsection
# Empecemos!
!SLIDE bullets incremental transition=fade

# 1) Creamos nuestra aplicación RoR:

!SLIDE 
	curl -O \
	https://raw.github.com/gist/1108601/eaa7979edf6ba2\
	e93880f6925a62498ae9b8ac8d/taller_setup.txt
	
    rails new mafalda -Tm taller-setup.txt


