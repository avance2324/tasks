
440  20220227A   regexp
--------------------------------------------------------------------
    [group     ] question
    [status    ] open
    [question  ] repace string
    	       	 1) syntax
		     re.sub(pattern, repl, string, count=0)
                     # count: number of occurance
                 2) camel to snake
		    value = re.sub(r'([a-z0-9])(A-Z)', r'\1_\2', value)
		 3) snake to camel
		    def replacement(match)
		    	return match.group(2).upper()
			
   		    value = re.sub(r'(_)([a-z])', replacement, value)
		    ## use reg.sub() function allow to use second
		    ## argument repl as function
        
        
        example
        ======================
        import re

## Note: reg.sub(pattern, repl, str )
##       allow the second argument repl to be a replacement function
##       This solve the problem of processing the match group
##       
def replacement(match):
    a = match.group(2).upper()
    return a

def snake_to_camel(value):
    value = re.sub(r'(_)([a-z])', replacement, value);

    return value


snake = "this_is_snake"
print(f"{snake} -> {snake_to_camel(snake)}")
print("wait")


