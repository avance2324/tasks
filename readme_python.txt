
440   20220223A  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 what is __init__.py ?
                 how to use it ?
		 <= in Python3.3 or early the __init__.py is used to mark
		    directories as python package directory.
		    see example:
		      my_dir/spam/__init__.py
		      my_dir/spam/module.py

                     
		    If set my_dir to your path
		     export PYTHONPATH=.../my_dir
		    then you can import the code in module.py like this:
		      import spam.module
		    or
		      from spam import moudle

                 <= the __init__.py is usually empty.   
		 <= after Python3.3, we don't need to use __init__.py
		    to indicate python package.
		    It can work without it.
		    However, the __init__.py will be the first
		    script to be run, therefore you can add some
		    code there like
		 <= for now, you can add some initial code to __init__.py
		    because __init__.py is executed prior to other
		    python code.
		    - from my_package.display_pkg import display_name
		    
		    
441   20220223B  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 what is __main__.py ?
    	      	 how to run __main__.py ?
		 <- normally you call python by
                     python3  mypro.py
		     
		 <- but if you have __main__.py in the my_dir,
		       my_dir/
		         __main__.py

                    the you can also run python like this:
		    
		     python3 -m my_dir

442   20220223C  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 if m_dir contains __init__.py and __main__.py, which
    	      	 is executed first ?


443   20220223D  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 difference between __init__.py and __main__.py
                 1) __init__.py:
		    it is run when you import a package into a running
		    python program
		      import idlelib within a program, run idlelib/__init__.py

                 2) __main__.py:
		    it runs as __main__ when you run a package as the
		    main program.
                      python3 -m idlelib
		      # run idlelib/__main__.py

444   20220223D  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 example of __main__.py
                 see example: tkinter/__main__.py
		    from . import _test as main
		 <- explanation:
		     1) . is the current folder tkinter
		     2)

445   20220223E  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 in python/tests/main/002, when I run following
    	      	 python3 program/__main__.py I got following error:
		   ImportError: attempted relative import with no
		   known parent package

		 <= in __main__.py I have following line

		    from . import _test as main

                    This means from the same directory as __main__.py
		    import
                 <- The difference between with and without -m options
		    is with -m, the package "program" is imported.
		    while without -m option, the package "program"
		    is not imported.
		    Therefore, 
    

446   20220223F  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 what does "python3 -m mod" mean?
    	      	 <- run library module as a script 


447   20220223G  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 why do we need "python3 -m module" to run library
                 module as a script? To debug/test library?
                 <- 1) if your run:
		           python3 -m module
		       python import package "module", and then run
		       the script module/__main__.py

                 <- 2) if your run:
		           python3 module
		       python will run script module/__main__.py
		       directly

		    you can prove this by adding following line
		    to __main__.py
		      print(f" package = {__package__}")

                    with -m option, you get package = module
		    without -m option, you get packag = ""
		    
                 <- Therefore, if your script __main__.py depends
		    on other files, we can use -m option to
		    import all files under dir/ 


448   20220223H  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [refer    ]	 python/tests/main/
    [task     ]	 how to use __init__.py
    	      	 1) place __init__.py in the package directory
		 2) "bring" functions to the package level
		     from .display_pkg import display_name
		     from .arith_pkg import  add 
		     from .arith_pkg import  sub
		      ...
		 3) in main.py

                     import libs
		     libs.add(2,3);


448.1   20220223I  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 open
    [task     ]	 how debug textparser ?
    	      	 <- 1) based on the error report, remove some words,
		       until there is no error?
		    2) check the parser why it works after removing
		       and why it doesn't work without 

449  20220227A   regexp
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



450   20220228A  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 open
    [task     ]	 some question about python
    	      	 1) getattr( object, str)
		     example-1: name = getattr(Tom, "name")
		     equivalent to name = Tom.name
    	      	     ## Tom = Person ("Thomas")
		     example-2: getattr(Tom, "set_id")(23)    
                     equivalent to Tom.set_id(23)
                 2) what is @property ?

		 3)    

451   20220304A  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 what is the meaning of variable or function with prefix
                 underscore in python class ?
		 >= This indicates the variable and function are for
		    internal use 

452   20220304B  python property
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [summary  ]	 1) protected variable starts with _
    	         2) @property # getter
		    @<var>.setter # setter
		    @<var>.deleter # deleter
    [task     ]	 use property to access protected variable in class
    	      	 see following example
                  class House:
                  
                  	def __init__(self, price):
                  		self._price = price
                  
                  	@property
                  	def price(self):
                  		return self._price
                  	
                  	@price.setter
                  	def price(self, new_price):
                  		if new_price > 0 and isinstance(new_price, float):
                  			self._price = new_price
                  		else:
                  			print("Please enter a valid price")
                  
                  	@price.deleter
                  	def price(self):
                  		del self._price		   


453   20220304F  python
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 open
    [task     ]	 what does underscore mean?
    	      	  https://dbader.org/blog/meaning-of-underscores-in-python#
		  :~:text=The%20underscore%20prefix%20is%20meant,
		  public%E2%80%9D%20variables%20like%20Java%20does.

