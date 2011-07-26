!SLIDE subsection

# Iteradores (Iterators)

!SLIDE bullets incremental
#Iteradores
* Parecidos a los loops
* Acceso a una colección de Datos
* Se sabe el inicio y el final de la colección de datos. No es necesario una condición para interrumpir la iteración.

!SLIDE 
	@@@ruby
	Loops
	
	c = 0 
	while c < 3		
		puts "Hola RailsBridge"
		c+=1
	end 
	
	Iteradores
	
	3.times{ puts "Hola RailsBridge"}
	
	Hola RailsBridge
	Hola RailsBridge
	Hola RailsBridge
	

!SLIDE
### Tenemos acceso a la variable dentro del bloque
	@@@ruby
	5.downto(1){|i| puts "Faltan #{i} segundos para Año Nuevo!"}
	
	Faltan 5 segundos para Año Nuevo!
	Faltan 4 segundos para Año Nuevo!
	Faltan 3 segundos para Año Nuevo!
	Faltan 2 segundos para Año Nuevo!
	Faltan 1 segundos para Año Nuevo!
	
	
!SLIDE
## El popular each, por cada elemento... 
    @@@ ruby
    animals = ["gato", "perro", "caballo"]
    animales.each do |animal|
      	#procesamos el elemento
		puts "Tenemos un " + animal
    end

!SLIDE
## Iteradores en hashes
    @@@ ruby
    my_hash = { :type => "cat",
                :name => "Beckett",
                :breed => "alley cat" }
    
	my_hash.each do |key, value|
      puts "My " + key.to_s + " is " + value
    end
!SLIDE
	@@@ruby
	my_hash.each_pair{|k,v| puts "key: #{k} con su valor: #{v}"}
	
	key: type con su valor: cat
	key: name con su valor: Beckett
	key: breed con su valor: alley cat

!SLIDE bullets incremental
## Iteradores en diferentes tipos de objetos

* Strings: each_line, each
* Hashes: each_value, each_pair, each, etc
* Array: each, each_index, each_with_index, etc
* Integers/Floats: upto, downto, times

	