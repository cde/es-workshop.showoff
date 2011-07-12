!SLIDE subsection

# Strings

!SLIDE
## Interpolation

    @@@ ruby
    "boyz #{1 + 1} men"
    => "boyz 2 men"

<div class="big-text">Cualquier código en ruby que va entre las {} se evalúa aunque este entre un string</div>

!SLIDE
#Interpolation ...

    @@@ ruby
    >> a = "mundo"
    >> puts "hola #{a}"
    hola mundo

    >> a = 2
    >> puts "hola #{a}"
    hola 2

    >> a = nil
    >> puts "hola #{a} que tal?"
    hello  que tal?
