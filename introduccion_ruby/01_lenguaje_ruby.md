<!SLIDE image center bullets incremental transition=fade>
# Ruby es un Lenguaje
<img src="/images/ruby-logo.jpg" width="125"  height="125" >

* Interpretado y Orientado a Objetos
* Aplicable a muchos dominios
* Flexible e Intuitivo
* Patrones Comunes


<!SLIDE bullets incremental transition=fade>
# Ruby
* Puede ser modificando en tiempo real
* De tipeo dinámico

!SLIDE bullets incremental transition=fade

* Blocks / lambdas / closures
* Parecido a Perl (expresiones regulares)
* Conectado cercánamente al shell & OS

<!SLIDE bullets incremental transition=fade>
#Ruby 
* Es Código Libre y Grátis (Open Source)
* Ruby 1.0 liberado en 1996 

!SLIDE 
# Ruby es interpretado

<!SLIDE bullets incremental transition=fade>
## Muchas implementaciones
* MRI
** REE
** Kiji
* JRuby
* Rubinius
* MagLev, MacRuby, IronRuby

!SLIDE subsection
# Versiones

!SLIDE bullets
# Versiones Comunes

* 1.8.7
* 1.9.2

!SLIDE bullets
# Versión Recomendada

* <strike>1.8.7</strike>
* **1.9.2**

!SLIDE center

[![RVM](/images/rvm-logo.png)](http://rvm.beginrescueend.com/)

## RVM es una herramienta que nos permite instalar, manejar y trabajar con diferentes versiones de ruby, desde interpretes a gemas.

!SLIDE
## Confirmemos la version de ruby. 

	rvm info
	.....
	ruby:
    	interpreter: "ruby"
    	version:     "1.9.2p290"
 	....
	homes:
	    gem:         "/Users/carmen/.rvm/gems/ruby-1.9.2-head@global"
	    ruby:        "/Users/carmen/.rvm/rubies/ruby-1.9.2-head"
	 
	 
!SLIDE subsection
# IRB: Interactive RuBy

!SLIDE

    @@@ ruby
    $ irb
    >> 4
    => 4
    >> 4+4
    => 8
