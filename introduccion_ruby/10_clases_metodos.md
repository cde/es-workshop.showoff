!SLIDE subsection

# Clases & métodos

!SLIDE subsection
# Clases

!SLIDE bullets incremental transition=fade
* Define qué es un Objeto?
* Define qué puede hacer el objeto?

!SLIDE
# Clases ... Qué es

    @@@ Ruby
    class User
    end

    u = User.new
    # => #<User:0x00000100999f70>

    u.class
    # => User

    u.is_a?(User)
    # => true

!SLIDE
# Clases ... Qué hace

    @@@ Ruby
    class User
	    def initialize(name)
	        @name = name
	    end

      	def name
	        @name
	    end
	
		def canta?
			true
		end
    end

!SLIDE commandline
    u = User.new
    # => ArgumentError: wrong number of arguments (0 for 1)

    u = User.new("Carmen")
    # => #<User:0x00000100999f70>

    p u.name
    # => "Carmen"
	u.canta?
	# => true


!SLIDE subsection
# Métodos

!SLIDE bullets
### En este taller hemos visto métodos pertenecientos al tipo de objeto. Ej 

	@@@ruby
	"rails bridge".capitalize
	 => "Rails bridge"
	
!SLIDE bullets
### Podemos definir propios métodos fuera de una clase
	
	@@@ruby
	>irb
	def saludar(nombre)
		puts "Hola #{nombre}"
	end
	=> nil
	
	y luego utilizarlo
	
	>saludar("Ana")
	=> "Hola Ana"

!SLIDE
### Métodos son útiles cuando es definido en una clase o  mixing (Qué hace la clase?)

    @@@ ruby
    class Thing
      def return_something
        "something"
      end
    end

!SLIDE

    @@@ ruby
    class Thing
      def do_something(a,b)
        a + b
      end
    end

 

!SLIDE
# Métodos

    @@@ Ruby
    class User
      # Instance method
      def name
      end

      # Class method
      def self.dance
      end
    end
<!SLIDE>
### Prueba por ti mismo
<div style="margin-left:25px; font-size:20px"> Abre el irb y construye lo siguiente:
<a href="http://www.wiki.devchix.com/index.php?title=Programming_intro">calculator.rb </a>("http://www.wiki.devchix.com/index.php?title=Programming_intro")</div>
	
	@@@ruby
	
	class Calculator	
		def describe
	    	"I am a really neat calculator!"
	   end

		def add(a,b)
			a + b
		end
   	end

