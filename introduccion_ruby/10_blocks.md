!SLIDE subsection
# Block

!SLIDE bullets incremental
# Block

* Métodos pueden tomar argumentos en el block
* Usa  `do...end` o `{...}` al final de la lista de argumentos
* Dentro del método, llama el block con 'yield'

!SLIDE
### Hemos estado utilizado code blocks durante el taller! 

	@@@ruby
	frutas = ["manzana", "banana"]
	frutas.each{|f| puts "Esta fruta se llama: #{f}"}
	
	frutas.each do |fruta|
		puts "Esta fruta se llama: #{fruta}"
	end	

!SLIDE
	
	Ambos code blocks retornan el mismo resultado:
	
	Esta fruta se llama: manzana
	Esta fruta se llama: banana
	 => ["manzana", "banana"]
	
!SLIDE
### Dentro del método, llama el block con 'yield'
 
	@@@ ruby
	def twice
	   yield
	   yield
	end

	twice do
	  puts "hi there"
	end
	
!SLIDE bullets incremental

* Blocks pueden también tomar parámetros y retornar un valor
* El iterador "map" translada cada elemento en un array

!SLIDE

    @@@ ruby
    ["hello", "world"].map{ |string| string.upcase }
    => ["HELLO", "WORLD"]
