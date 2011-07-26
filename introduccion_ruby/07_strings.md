!SLIDE subsection

# Strings

!SLIDE 
#Strings... algunos métodos
	@@@ruby
	"hola".upcase 
	=> "HOLA"
	
	

!SLIDE
## Interpolation

    @@@ ruby
    "Tenemos #{1 + 1} voluntarios"
    => "Tenemos 2 voluntarios"

<div class="big-text">Cualquier código en ruby que va entre las {} se evalúa aunque este entre un string</div>

!SLIDE
#Interpolation ...

    @@@ ruby
    >> a = "mundo"
    >> puts "hola #{a}"
    hola mundo

    >> a = 2
    >> puts "hola #{a}"
    hola 2

    >> a = nil
    >> puts "hola #{a} que tal?"
    hola  que tal?
