!SLIDE subsection
# Symbols

!SLIDE bullets incremental 
#:a_symbol
* Es una etiqueta (label) que será utilizado para identificar una parte de la información.

* No son variables, son etiquetas y pueden ser usados como keys en un hash.
* Parecido a strings pero son diferentes

!SLIDE
#:a_symbol
<div class="big-text"> Existe sólo una representación de un símbolo en memoria para el interpreter ruby ":a_symbol" </div>
<div class="big-text"> En Ruby, preferimos simbolos sobre variables globales y strings, ya que son muy ligeros. </div>

!SLIDE bullets incremental
* El símbolo va a ser guardado en memoria una sóla vez. 
* En cambio, el string es guardado en memoria todas las veces.


!SLIDE
# Prueba tu mismo
	@@@ruby
	> irb
	:animal	 
	=> :animal
	:animal.object_id
	=> 456168 
	
	"animal"	 
	=> "animal"
	"animal".object_id
	=> 2156252700 	 
!SLIDE
# El Object_id del symbol no cambia  
	@@@ruby
	> irb
	:animal	 
	=> :animal
	:animal.object_id
	=> 456168 

	"animal"	 
	=> "animal"
	"animal".object_id
	=> 2156181200 	 

!SLIDE
## Etiquetas (labels) en un hash
### Un poco más adelante verás con detalle el hash.

	@@@ruby
	persona = {:nombre => "Carmen" :nickname => "póra"}

