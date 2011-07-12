!SLIDE subsection

# Clases & métodos

!SLIDE subsection
# Clases

!SLIDE bullets incremental transition=fade
* Define qué es un Objeto?
* Define qué puede hacer el objeto?


!SLIDE
# Clases

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
# Clases

    @@@ Ruby
    class User
      def initialize(name)
        @name = name
      end

      def name
        @name
      end
    end

    u = User.new
    # => ArgumentError: wrong number of arguments (0 for 1)

    u = User.new("Carmen")
    # => #<User:0x00000100999f70>

    p u.name
    # => "Carmen"

!SLIDE

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

!SLIDE subsection
# Métodos


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
