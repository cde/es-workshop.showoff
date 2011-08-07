!SLIDE  subsection
# Variables

!SLIDE
# Las variables son implícitas y declaradas

    @@@ ruby
    nombre = "Santa"
    apellido = "Claus"
    nombre_completo = nombre + apellido
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

# Built-in Tipos de Objetos

* Symbols
* Arrays
* Hashes
* Strings
* FixNum