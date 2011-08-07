!SLIDE subsection
# Hash

!SLIDE bullets incremental
# Hash
* Similar a los arrays
* Colección de objectos no ordenados
* Localización de los elementos a través de los objetos (key-value pair)

!SLIDE bullets incremental
#conocido también como...

* Map
* Associative Array
* Dictionary
* Key/Value Pair Store

!SLIDE bullets incremental
# Hash
### Puede ser definido "literalmente" (en linea)

    @@@ ruby
    letras_frutas = {"A" => "anana",
    "B" => "banana", "C" => "coco"}


!SLIDE
### ... o definiendo un instancia

    @@@ ruby
	states = {}
	=> {}
	states.class
	=> Hash
	
	states =  Hash.new
	=> {}
	states.class
	=> Hash
	
!SLIDE
### Populando / alimentando el hash 
	@@@ruby 	
    states = {"MA" => "Massachusetts",
              "CA" => "California"}
	 => {"MA"=>"Massachusetts", "CA"=>"California"} 

!SLIDE
### .. Populando / alimentando el hash 
	@@@ruby
	states["NY"] = "New York"
	=> {"MA"=>"Massachusetts", "CA"=>"California",
	"NY"=>"New York"}
			
!SLIDE 
### Se accede por el "key"
 
	@@@ruby
    states["MA"] #=> "Massachusetts"

!SLIDE 
### Se accede por el "key" 
	@@@ruby
	states.values_at["CA"] #=> "California"

!SLIDE
### Mixed hash, diferentes tipos de objetos
	@@@ ruby
	mixed = { 2 => ["dos", "two", "deux" ], 3 => "tres",
	:precio => 45.4", "un_string" => "hola"}

!SLIDE
	@@@ ruby
	mixed.keys
	 => [2, 3, :precio, "un_string"] 
	
	mixed.values
	 => [["dos", "two", "deux"], "tres", 45.4, "hola"]	