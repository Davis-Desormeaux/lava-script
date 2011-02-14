# LavaScript

A lispy language that compiles into JavaScript.

## The code

See [lava.coffee](https://github.com/evanrmurphy/lava-script/blob/master/lava.coffee).

## Todo

- the rest of the compiler core (lc)
- the reader (consider using the reader from [Lispy](http://norvig.com/lispy2.html) as a guide)
- macro system
- pretty-printed output
- npm packaging

## The language

LS on the left, JS on the right in the examples below.

### Numbers

    1                          1
    42                         42
    3.14159265                 3.14159265

### Strings

    "a"                        "a"
    "do re mi"                 "do re mi"

(Strings are always double-quoted, because single-quotes are reserved for `quote`ed symbols.)

### Assignment

    (= meaning 42)             meaning = 42;

### Arrays

    (= a [1 2 3])              a = [1, 2, 3];

    ([0] a)                    a[0]
    (ref a 0)                  a[0]

### Objects

    (= o {a 1 b 2})            o = {a: 1, b: 2};
  
    o.a                        o.a
    (.a o)                     o.a
    (['a] o)                   o['a']
    (ref o 'a)                 o['a']

### Conses

    (cons 1 nil)               [1, nil]
    (cons 1 (cons 2 nil))      [1, [2, nil]]
    (list 1 2)                 [1, [2, nil]]
    '(1 2)                     [1, [2, nil]]
  

### Functions
  
    (= add1 (fn (x) (+ x 1)))  add1 = function(x) { return x + 1; };

    (add1 5)                   add1(5);

    (def add2 (x) (+ x 2))     add2 = function(x) { return x + 2; };

### Chaining

    (chain ($ "a") click       $("a").click(function() {
      (fn ()                     return alert("clicked");
        (alert "clicked")))    })();

### Macros

    (mac $ (selector . args)
      `(chain (jQuery ,selector) ,@args))

    ($ "a" click (fn ()        jQuery("a").click(function() {
      (alert "clicked"))         return alert("clicked");
                               })();



  

