!SLIDE subsection

# Iteradores (Iterators)

!SLIDE

    @@@ ruby
    my_array = ["cat", "dog", ”world"]
    my_array.each do |item|
      puts "hello " + item
    end

!SLIDE

    @@@ ruby
    my_hash = { :type => "cat",
                :name => "Beckett",
                :breed => "alley cat" }
    my_hash.each do |key, value|
      puts "My " + key.to_s + " is " + value
    end
