!SLIDE subsection
# Arreglos (Array)

!SLIDE bullets incremental
# Arreglos (Array)
* Dinámicamente ajustable (longitud, tamano del array)
* Contiene diferentes tipos de datos
* Indice empieza en cero
* Puede ser definido literalmente (en linea). Ej.

!SLIDE
# Array

    @@@ ruby
    fruits = ["apple", "banana"]

!SLIDE

    @@@ ruby
    a = [1, 2, 3]
    a.push "four" #=> [1, 2, 3, "four"]
    a.pop #=> "four"
    a[0] #=> 1

!SLIDE execute

# Executable Ruby #

	@@@ ruby
	result = [1, 2, 3].map { |n| n*7 }

!SLIDE subsection
# Hash

!SLIDE bullets incremental

# Hash

#conocido tambien como...
* Map
* Associative Array
* Dictionary
* Name/Value Pair Store
* Key/Value Pair Store

!SLIDE incremental

# Hash

# Puede ser definido "literalmente" (en linea)

    @@@ ruby
    letter_fruits => {"A" => "apple",
    "B" => "banana"}


!SLIDE

    @@@ ruby
    states = {"MA" => "Massachusetts",
              "CA" => "California"}

    states["MA"] #=> "Massachusetts"

!SLIDE

    @@@ ruby
    my_hash = {:a_symbol => 3, "a string" => 4}
    my_hash[:a_symbol] #=> 3
