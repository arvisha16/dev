# PHP #

## Minimal Example Code ##
In order for the PHP code to be interpreted correctly, the filename must end with ".php".

    <!-- Displays "Hello, World!" -->
    <p>
        Hello, <?php echo "World"; ?>!
    </p>


## Basics ##
- Variables always start with a `$` sign.
- Single-line PHP code doesn't need a semi-colon at the end of lines, but multi-line PHP code does.
- PHP comments can either be single line with `//` or multi-line with `/* comment */`.
- Extra whitespace mostly doesn't matter, but is useful for readability.

    <?php 
        $name = "Dan";
        $full_name = "Danial Goodwin";
    ?>
    <?php echo $name ?>

### Datatypes ###
- Seven data types: integer, float, string, array, boolean, object, resource.
- String are zero-based index.
- Use `\n` to create a newline, aka just like an HTML `<br />`.

	    <?php
	        $one = 1; // integer
	        $two = "2"; // string (same as a byte)
	        $pi = 3.14; // float
	        
	        echo gettype($one); // Outputs "integer".
	        echo gettype($two); // Outputs "string".
	        echo gettype($pi); // Outputs "double".
	        
	        echo $one + $one; // Outputs 2.
	        echo $one + $two; // Outputs 
	        echo $one + $pi; // Outputs 4.14.
	        
	        $greeting "Hello, World!";
	        echo $greeting{1}; // Outputs "r".
	        $greeting{0} = "J";
	        echo $greeting; // Outputs "Jello, World!".
	        
	        $bool = TRUE;
	        $foo = FALSE;
	        var_dump($bool); // Outputs "bool(true);
	        var_dump((bool) ""); // Outputs "false".
	        var_dump((bool) 0); // Outputs "false".
	        var_dump((bool) 0.0); // Outputs "false".
	        var_dump((bool) array()); // Outputs "false".
	        var_dump((bool) "abc"); // Outputs "true".
	        var_dump((bool) -1); // Outputs "true".
	        isset($foo); // Outputs "false";
	        
	        // Constants, should be all caps for best practice. No $ needed. Can't start with a number.
	        define("YEAR", 2014);
	        define("SITE_NAME", "Simply Advanced");
	        echo YEAR;
	        echo SITE_NAME;  
	        
	        // Arrays. Zero-based index. Can have mixed datatypes.
	        $empty_array = array();
	        $names = ['dan', 'chris', 'joe', 12, 3.14, TRUE]; // Shorthand.
	        echo $names[5]; // Outputs 1.
	        $names = array('dan', 'chris', 'joe'); // Can use single or double quotes.
	        print_r($names);
	        echo $names[0]; // Outputs "dan".
	        $names[1] = "Lola";
	        $names[] = "Yoda"; // Adds another element at the end.
	        
	        // Associative Arrays.
	        $things = array(
	            'foo_key' => 'foo_value',
	            'bar_key' => 'bar_value'
	        );
	        print_r($things);
	        echo $things['foo_key']; // Outputs "foo_value".
	        $things['foo_key'] = 'asdf'; // Re-asign value.
	        $things['new_key'] = 'new_value'; // Adds another element at the end.
	    ?>

### Operators ###
- Three types of operators: unary, binary, ternary. And, they operate on one, two, or three variables.
- Assignment: 
- Comparisons: 
- Concatenation: `.`
- Arithmetic: 
- Casting: 

	    <?php
	        $a = 10;
	        $b = 10;
	        
	        $sum = $a + $b;
	        $diff = $a - $b;
	        $product = $a * $b;
	        $quotient = $a / $b;
	        
	        $sum = $sum + 1;
	        $sum++; // Auto-increments by one.
	        $sum--; // Auto-decrements by one.
	    ?>
	    
	    <?php
	        $a = 10;
	        $b = 10;
	        $c = 20;
	        $d = "10";
	        
	        var_dump($a == $b); Outputs bool(true);
	        var_dump($a != $b); Outputs bool(false);
	        var_dump($a != $c); Outputs bool(true);
	        var_dump($a === $b); Tests identical, outputs bool(true);
	        var_dump($a === $d; Tests identical, outputs bool(false);
	        var_dump($a !== $b); Tests identical, outputs bool(false);
	        
	        var_dump($a < $b); // Is a less than b, false;
	        var_dump($a > $b); // Is a greater than b, false;
	        var_dump($a <= $b); // Is a less than or equal to b, true;
	        var_dump($a >= $b); // Is a greater than or equal to b, true;
	    ?>
	    
	    <?php
	        $a = TRUE;
	        $b = TRUE;
	        $c = FALSE;
	        var_dump($a and $b); // true
	        var_dump($a and $c); // false
	        var_dump($a or $c); // true
	        var_dump($a && $c); // false, same as using 'and'
	        var_dump($a || $c); // true, same as using 'or'
	        var_dump(!$a); // false
	    ?>

### Conditionals & Loops ###
- Conditionals: if, elseif, else
- Loops: for, foreach, while, do-while

	    <?php
	        if () {
	            // Code to run.
	        } elseif(){
	        
	        } else {
	        
	        }
	    ?>
	
	    <?php
	        define("USE_FULL_NAME", TRUE);
	        $first = "Danial";
	        $last = "Goodwin";
	        
	        if(USE_FULL_NAME == TRUE){
	            $name = $first . ' ' . $second;
	        } else {
	            $name = $first;
	        }
	        
	        if($name == 'Danial'){
	            $info = "OK";
	        } elseif($name = 'Danial Goodwin'){
	            $info = "NO OK";
	        } else {
	            $info = "NO";
	        }
	    ?>
	
	    <ul>
	        <?php
	            $max = 10;
	            for($counter=1; $counter <= $max; $counter++){
	                echo "<li>" . #counter . "</li>";
	            }
	        ?>
	    </ul>
	
	    <ul>
	        <?php
	            $things = array('foo', 'bar', 'lola');
	            foreach($things as $thing){
	        ?>
	            <li><?php echo $thing ?></li>
	        <?php
	            }
	        ?>
	    </ul>


## Further Resources ##
- 