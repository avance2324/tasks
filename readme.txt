		 ================================
		 Method-2: use docker extension
		 ================================
		   1) start docker container
		   2) start vscode in host
		   3) in vscode click docker extension
		   4) in left window under DOCKER/CONTAINERS, right click the run container
		        -> Attach Visual Studio Code
		      <- it will open a vscode window with title:
		         ...[Container ....4.2.11-opengl ...]
	           5) open file and set breakpoint (main.py)
		   5) press F5
		  # In testbench case, sometimes shows
		    No module named "MRMCommand_pybind"
		    just close the debugger, and run . .envrc and press F5 again.
		    you should be able to debug it.




     3.  how to debug python code in oocker
---------------------------------------
    in .vscode/
    ln -s launch_docker.json launch.json    
    code .
    in terminal, type . build.scr
    open test_magic.py
    set break point
    press F5 to debug  

                


question/notes
=========================================================
1.  how to tell cffi to build wrapper based on shared library?
    <= see cffi/build_wrapper_magic.py
          ffibuilder.set_source("_magic",
          f"""
              #include "{header}"
          """,
          include_dirs = ['../c/include/'],
          library_dirs = ['../c/build/'],
          libraries=[ 'magic' ],)

2.  which environment variable should be set in order to run cffi wrapper ?
    <= see set_path.scr  
        export PYTHONPATH = ./cffi
        export PYTHONPATH = ./c/build 
        export LD_LIBRARY_PATH = ./c/build  ## because libmagic.so is here!

3.  why I need to set up LD_LIBRARY_PATH ?
    <= because the cffi wrapper is built from libmagic.so, 
       in the generate wrapper _magic.**.so, it doesn't tell where is 
       the c source code and header (use strings to check)
       Therefore we need to tell the python the location of libmagic.so 
       via LD_LIBRARY_PATH

4.  how do I create this testcase
    <= see following
       1) copy from /home/fjxvn4/svn_client/my_tools/trunk/python/cffi/006_use_so/

       2) copy following file from ../014_debug_c_in_container_cffi/
           - Dockerfile
           - requirement.txt
           - run_001_build_image.scr
           - run_002_run_container.scr
           - clean.scr

       3) make following changes
           - run_001_build_image.scr : change image name to *_cffi_so
           - run_002_run_container.scr : change container name to *_cffi_so
           - clean.scr: change image and container name to *_cffi_so
           - .vscode/launch_docker.json:  "program": "/usr/local/bin/python3",
              "environment": [{"name":"PYTHONPATH","value":"${workspaceFolder}/../cffi"}, 
                              {"name":"LD_LIBRARY_PATH","value":"${workspaceFolder}/build"}],       
           - in .vscode: ln -s launch_docker.json  launch.json
           - in Dockerfile: add && apt install -y cmake \

summary of the week 20220305 - 20220312
1.   update docker image with LAN 1hour is much faster
2.   cmake ../ -DCMAKE_BUILD_TYPE=Debug
3.   cmake --build . ## == make 
4.   standard project structure using CMakeLists.txt 
      https://github.com/Barthelemy/CppProjectTemplate
      use add_subdirectory(<dir_name>) to realize the structure      
5.    c: initialize array and structure 
       int x[] = {1,2,3}
       Person m  = {
            .firstname = "John\0",
	    .lastname = "McCarthy\0",
	    .age = 24
	 };
6.    get langth of array of struct
       sizeof(ar) / sizeof(ar[0]);
7.    debug c in docker (cmake ../ -DCMAKE_BUILD_TYPE=Debug)
8.    how to know if a .so is build from debug for release ?
        strings *.so | grep -i debug
9.    convert relative path to absolute path in python 
       using string "AbW5zrsYqlrEiPnDtFRlz9G57fpN0wS"
