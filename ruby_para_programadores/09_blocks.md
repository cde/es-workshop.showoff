!SLIDE subsection
# Block

!SLIDE bullets incremental
# Block

* Métodos pueden tomar argumentos en el block
* Usa  `do...end` o `{...}` al final de la lista de argumentos
* Dentro del método, llama el block con 'yield'

!SLIDE

    @@@ ruby
    my_array = ["cat", "dog", ”world"]
    my_array.each do |item|
      puts "hello " + item
    end

!SLIDE

    @@@ ruby
    def twice
       yield
       yield
    end

    twice do
      puts "hi"
    end

!SLIDE bullets incremental

* Blocks pueden también tomar parámetros y retornar un valor
* El iterador "map" translada cada elemento en un array

!SLIDE

    @@@ ruby
    ["hello", "world"].map{ |string| string.upcase }
    => ["HELLO", "WORLD"]
