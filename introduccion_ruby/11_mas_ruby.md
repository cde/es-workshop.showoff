!SLIDE subsection

# Más interesantes puntos sobre ruby

!SLIDE image center
<img src="/images/duck_typing.jpg" width="250">
!SLIDE bullets incremental transition=fade
# duck typing

* Si se parece a un pato,
* suena como pato...
* No nos interesa cómo un objeto es, siempre y cuando haga lo que querramos.

!SLIDE

    @@@ ruby
    def print_even_or_odd(array_like_thing)
      array_like_thing.each do |item|
        puts "#{item} is #{item.even? ? "even" : "odd"}."
      end
    end

!SLIDE

    @@@ ruby
    print_even_or_odd [1, 2, 3]
    print_even_or_odd 1..3

!SLIDE

# Modules and Mixins
<div class="big-text"> Ruby tiene un sistema de herencia mixta, parecido a la herencia múltiple con una clase ancestro primordial.</div>

!SLIDE bullets incremental transition=fade

# ruby avanzado

* meta-programming
* Domain-Specific Languages (DSLs)

!SLIDE bullets incremental transition=fade

#Rails
#Rake
#Cucumber
#Rspec
#etc


!SLIDE bullets incremental transition=fade

# Privado vs Publico (private vs public)

* Ruby no provee realmente mucha protección
* Private significa "Por favor, no entre."
* Si alguien tiene acceso a tu ambiente de ejecución (runtime), significa que es de confianza
* Pasa el tiempo codificando (y escribiendo pruebas), no protegiendote de otro código.

!SLIDE
# Reabriendo clases

    @@@ ruby
    class Fixnum
      def even?
        self % 2 == 0
      end
    end

    1.even? #=> false

!SLIDE
# Todo es un objeto

!SLIDE bullets incremental transition=fade

# Clases son objetos

* class methods son realmente métodos de la clase "objeto"
* código evaluado en el alcance de la definición de una clase actua en la clase "objeto"




