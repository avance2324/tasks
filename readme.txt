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


docker run  \
    -it \
    --ipc host \
    --net host \
    --rm \
    $GPUS \
    --privileged \
    --device /dev/dri \
    --entrypoint /my/entrypoint.sh \
    -e DISPLAY=$DISPLAY \
    -e HOME=/home/xxx \
    -e XAUTHORITY=$XAUTHORITY \
    -e TERM=xterm-256color \

     

                

