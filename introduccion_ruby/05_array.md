!SLIDE subsection
# Arreglos (Array)

!SLIDE bullets incremental
# Arreglos (Array)
* Colección ordenada de objetos (puede ser de diferentes tipos)
* Posición dinámicamente ajustable (tamaño del array) 
* Indice o posición empieza en cero
* Puede ser definido literalmente (en linea). Ej.


!SLIDE
# Array - Notacion
	@@@ ruby
	frutas = Array.new
	# => []

!SLIDE
# Array - Notación
	@@@ ruby
	frutas = []
	# => []
	
!SLIDE
# Array
	
	@@@ ruby   
    frutas = ["manzana", "banana"]
	# => ["manzana", "banana"] 

!SLIDE
# Array

	@@@ ruby   
	frutas = %w{manzana banana}
	# => ["manzana", "banana"] 


!SLIDE bullets incremental
### Elementos en el array pueden ser de diferentes tipos
* Strings
* Otros arrays
* Numeros
* Otros objetos / clases


!SLIDE
	@@@ ruby
	myarray = [1,2,"tres", [4,5,"seis"], "frutas"]

!SLIDE

    @@@ ruby
    a = [1, 2, 3]
    a.push "cuatro" #=> [1, 2, 3, "cuatro"]
    a.pop #=> "cuatro"
    a[0] #=> 1

