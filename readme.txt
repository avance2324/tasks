521  20220212A   git merge
--------------------------------------------------------------------
    [group    ]  question
    [status   ]  open
    [reference]  
    [question ]  what is merge request and pull request?
                 <- merge request is from gitlab
		    pull request is from github
		    means of pulling changes from another branch
		    and merge the changes with your existing code.

522  20220212B   gitlab  
--------------------------------------------------------------------
    [group    ]  question
    [status   ]  closed 
    [reference]  
    [question ]  how to configure my git ?
    	      	 currently the file  ~/.gitconfig shows:
		   [user]
		       email = advance@email.com
		       name = advance

                 change it with following commands:
		   git config --global user.name "<name>"
		   git config --global user.email "<email>"


		 Now the ~/.gitconfig becomes:
		 
		   [user]
		       email = <email>
		       name = <name>

convert idl to cpp, .h



20220303A
     how to fetch remove branch 
       git pull --all 
       git checkout  <branch_name> ## you can get branch name in github/gitlab
       
20220303B
     gitlens tab is missing 
     <= Ctrl + Shift + P -> type Gitlens: show welcome view -> click Welcome
     
20220304
     gitlens questions
     
     
     545   20220303C  gitlens vscode
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 open
    [task     ]	 several questions on gitlens in vscode
                 0) how to enable git graph?
		    <- click in source control -> click repo -> click gitgraph		    
    	      	 1) how to create branch
		       gitgraph -> right click a commit -> create branch 
		    <- in COMMIT -> right click a commit -> create branch
		    
		 2) how to switch branch
		    <- in gitgraph -> right click the branch -> check out branch
		    <- in BRANCH -> right click branch -> switch to branch
		    
		 3) how do I know in which is my HEAD ?
		    <- click source control -> BRANCH -> the branch ticked
		       with v is HEAD
                    <- in gitgraph, the the BRANCH with O left to it
		       is the branch with header
		       
		 4) how to enable gitlens tab
		    <- Ctrl + Shift + P -> Gitlens: Show Welcome View
		    
		 5) how to compare branchs
		    <- in BRANCH -> right click a branch -> select for compare
		       right click another branch -> compare with selected
		       Then you will see a section in created under SEARCH & COMPARE
		       
		 6) how to compare commits
		    <- in COMMITS -> right click a commit -> select for compare
		       right click anoter commit -> compare with selected
		       it will create anoter section of comparison
		       
		 7) how to search commit based on: message, author
		    <- in SEARCH & COMPARE click + -> Search Commits ->
		        Search by Message, Author, Files, Changes ... 
		    
		 8) how to show graph
		    <- click Source Control -> View Git Graph
		    
		 9) how to checkout branch from remote
		    <-  git pull --all
		        git checkout <branch name>
                     
		10) how to know the branch name (especially remote branch) ?
		    <- git branch -a
		       feature/name_1
		       remote/feature/name_2

		       The branch name is the branch name execluding the
		       string "remote", such as 
		         feature/name_1,  feature/name_2

		11) how to open the branch in gitlab page?
		    <- click earth icon on branch, then enter, you
		       are brought to the gitlab page
		       
    	        12) how can I know the change of one commit?
		     <- with git graph, click the commit,
		       you will get a tree of file that are changed.
		         folder_1/
			   |
			   +-- file_A
			   |
                           +-- file_B
			   
                        click on the file, you will get the diff
                        ## you can select file list view
	             <-

                13) what are displayed when you compare branch A vs B?
		    assuming the common commit of A and B are C
		   
		      1) Behind/
		          B - C
	              2) Ahead
		          A - C
	              3) file change
		          A != B


                      C <-- A  (for Ahead)
		      |
		      +-<-- B  (for behind))

                     when you compare A vs B, Ahead means how much
		     A has been update


546   20220304A  vscode
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 open
    [task     ]	 how can I know the path for file in vscode?
    	      	 <- under the file tab, you will see the path
		     generator > database > __init__.py > load_file


550   20220304D  jira
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 in active sprint, how can I show or hide the
                 detail view
		 <- click Board -> Hide/Show detail view


551   20220304E  gitlab
--------------------------------------------------------------------
    [group    ]  quetion
    [status   ]	 closed
    [task     ]	 what does /-/blob following gitlab link mean?
                    /-/blob/master/src/test.py
                 -> I guess this is related to top of the branch
		    master
		 <- Yes, it is the link to the file task.py in
		    branch master
                

