
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

441  __getattr__()
# use of __getattr__()
#   When attribute x.y is accessed but not found by the usual procedure 
#   , Python calls x .__getattr__('y') instead
#   Then in __getattr__(self, y), python get the value of 'y' from 
#   somewhere else.
#   
#   
#   When you want to access test.y, and y is not defined in the class,
#   then python will report error: 
#    AttributeError: 'Test' object has no attribute 'y'
#   
#   By using __getattr
#   python will try to call __getattr__('y'), and return the value of 
#   test.x
#   
#  how to test
#  1) comment the part-1, you will get AttributeError: 'Test' object has no attribute 'y'
#  2) uncomment the part-1, you will get test.y = mytest_0
#
#
class Test:
    def __init__(self, x):
        self.x = x

    def display_val(self):
        print(f"x = {self.x}")

    # part-1
    def __getattr__(self, y):
        return self.x


test = Test("mytest_0")


print(f"test.y = {test.y}")

test.display_val()

print("wait")



20220304A
   debug docker container with vscode 
    
   {
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: Remote Attach",
            "type": "python",
            "request": "attach",
            "connect": {
                "host": "localhost",
                "port": 5679
            },
            "pathMappings": [
                {
                    "localRoot": "${workspaceFolder}",
                    "remoteRoot": "."
                }
            ]
        }
      ]
    }
