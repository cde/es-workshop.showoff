!SLIDE  subsection
# Variables

!SLIDE
# Las variables son implícitas y declaradas

    @@@ ruby
    first_name = "Santa"
    last_name = "Claus"
    full_name = first_name + last_name
    #=> "SantaClaus"

!SLIDE
# Scoping (Alcance)

    @@@ ruby
    var
    @var
    @@var
    $var
    VAR

!SLIDE
# Scoping (Alcance)

    @@@ ruby
    var   # puede ser una variable local
    @var  # variable de instancia
    @@var # variable de clase
    $var  # variable global 
    VAR   # constante

!SLIDE bullets

# Built-in Tipos de Datos

* Symbols
* Arrays
* Hashes
* Strings