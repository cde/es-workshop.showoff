!SLIDE

# Todo es un Objeto

!SLIDE

    @@@ ruby
    "test".upcase
    "test".class
    "test".methods
    2.methods
    1.to_s    #=> "1"
    "1".to_i  #=> 1

!SLIDE

# Todo evalua a algo

!SLIDE

    @@@ ruby
    >> 2 + 2
    => 4
    >> (2+2).zero?
    => false

!SLIDE

# Métodos son Mensajes

!SLIDE

    @@@ ruby
    thing.do(4)
    thing.do 4
    thing.send "do", 4

!SLIDE

# Operadores son Métodos

!SLIDE

    @@@ ruby
    1 + 2
    1.+(2)
    1.send "+", 2


!SLIDE
# Los comentarios son hechos con Hash, como en perl

    @@@ ruby
    # comentario
    2 + 2 # aqui va otro comentario

!SLIDE

# Ruby está inspirado para ser elegante y fácil de leer

# asi que puntuaciones y burocracias son mínimos.

!SLIDE

# punto y coma (semicolons), parentesis y `return` son opcionales

<div class="big-text"> Estas definiciones son equivalentes: </div>

    @@@ ruby
    def inc x
      x + 1
    end

    def inc(x)
      return x + 1;
    end

    def inc(x); x + 1; end

!SLIDE

    @@@ ruby
    >> "Hello".gsub 'H', 'h'
    => "hello"

    >> "Hello".gsub("H", "h").reverse
    => "olleh"


    
