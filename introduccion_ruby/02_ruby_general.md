!SLIDE

# Todo es un Objeto

!SLIDE

    @@@ ruby
    "test".upcase #=> "TEST"
    "test".class  #=> String
    1.to_s    #=> "1"
    "1".to_i  #=> 1
	1.class   #=> Fixnum


		
<!SLIDE transition=fade>
## Representan objetos del mundo real
<img src="/images/estudiante.jpg" >
	
	@@@ruby
	class Estudiante
		def nombre
			"Pepe"
		end
	end


!SLIDE bullets incremental 
## Lo que manipulas es un objeto.

	@@@ ruby
		2 + 2 #=> 4
		2.class #=> Fixnum

!SLIDE bullets incremental 
## Lo que se retorna es un objeto 
	@@@ruby
		2 + 2 #=> 4
		4.class #=> Fixnum
	
!SLIDE

# Todo evalúa a algo

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

!SLIDE bullets incremental transition=fade

# Ruby está inspirado para ser elegante y fácil de leer 
* asi que puntuaciones y burocracias son mínimos.

!SLIDE bullets incremental transition=fade

# punto y coma (semicolons), parentesis y returnos (return) son opcionales

!SLIDE
### Estas definiciones son equivalentes:

    @@@ ruby
    def inc x
      x + 1
    end

    def inc(x)
      return x + 1;
    end

    def inc(x); x + 1; end


    
