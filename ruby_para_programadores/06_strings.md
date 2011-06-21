!SLIDE subsection

# Strings

!SLIDE
## interpolation

    @@@ ruby
    "boyz #{1 + 1} men"
    => "boyz 2 men"

<div class="big-text">Cualquier codigo en ruby que va entre las {} se evalua aunque este entre un string</div>

!SLIDE
#String ...

    @@@ ruby
    >> a = "world"
    >> puts "hello #{a}"
    hello world

    >> a = 2
    >> puts "hello #{a}"
    hello 2

    >> a = nil
    >> puts "hello #{a} there"
    hello  there
