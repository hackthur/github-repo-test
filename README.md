# github-repo-test



## Commands

```bash
❯ git status
❯ git add <filename>
❯ git blame <filename>
❯ git hash-object <filename>
❯ git hash-object file-1.txt
❯ git branch -a
❯ git remote show origin 
❯ git tag --sort=-version:refname
❯ git log --oneline --decorate --graph --all
```




## Making a blob object

```bash
❯  echo "test content"
test content
## creating a new blob object and store it 
❯ echo "test content" | git hash-object --stdin -w
d670460b4b4aece5915caf5c68d12f560a9fe3e4

## reading the blob object
❯ git cat-file -p d670460b4b4aece5915caf5c68d12f560a9fe3e4
test content

## checking the file type of that object
❯ git cat-file -t d670460b4b4aece5915caf5c68d12f560a9fe3e4
blob
❯ git cat-file -t d670460b4b4aece5915caf5c68d12f560a9fe3e4
blob
❯ git add README.md
❯ git commit -m "new commands included in the README file"
[main 83ea7e1] new commands included in the README file
 1 file changed, 33 insertions(+)
❯ echo "version 1" > test.txt
## creating new file and store its hash into .git/objects
❯ git hash-object test.txt -w
83baae61804e65cc73a7201a7252750c76066a30
❯ tree .git/objects
.git/objects
├── 15
│   └── ac1ebe491c0a8e8c2b6c9de3accf8e8cac3532
├── 1e
│   └── b31dbe0053ccc4fddef8f55a8871f17f574ed5
├── 3c
│   └── eeddcb984b9d0571800647e13e5337836b267a
├── 66
│   └── 65bc4111fe631054264bccddfa291bee419e1b
├── 83
│   ├── 92e86101a6d02ca35eabb0eba8f501705a040c
│   ├── baae61804e65cc73a7201a7252750c76066a30
│   └── ea7e1726a97fec72c1c2f50e01c87731d0cbd2
├── 93
│   └── e8db87f6f7b846179cdb540d6fbde3d2822af3
├── bb
│   └── 4c05b81c93eae14a463343d4521d6652f8db6f
├── d6
│   └── 70460b4b4aece5915caf5c68d12f560a9fe3e4
├── ed
│   └── 5a7803ae42fa34d3583cb3ecd8ed851b09a21b
├── info
└── pack

12 directories, 11 files
❯ echo "version 2" > test.txt
❯ git hash-object -w test.txt
1f7a7a472abf3dd9643fd615f6da379c4acb3e3a
❯ tree .git/objects
.git/objects
├── 15
│   └── ac1ebe491c0a8e8c2b6c9de3accf8e8cac3532
├── 1e
│   └── b31dbe0053ccc4fddef8f55a8871f17f574ed5
├── 1f
│   └── 7a7a472abf3dd9643fd615f6da379c4acb3e3a
├── 3c
│   └── eeddcb984b9d0571800647e13e5337836b267a
├── 66
│   └── 65bc4111fe631054264bccddfa291bee419e1b
├── 83
│   ├── 92e86101a6d02ca35eabb0eba8f501705a040c
│   ├── baae61804e65cc73a7201a7252750c76066a30
│   └── ea7e1726a97fec72c1c2f50e01c87731d0cbd2
├── 93
│   └── e8db87f6f7b846179cdb540d6fbde3d2822af3
├── bb
│   └── 4c05b81c93eae14a463343d4521d6652f8db6f
├── d6
│   └── 70460b4b4aece5915caf5c68d12f560a9fe3e4
├── ed
│   └── 5a7803ae42fa34d3583cb3ecd8ed851b09a21b
├── info
└── pack

13 directories, 12 files
❯ rm test.txt
❯ git cat-file -p 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a
version 2
❯ git cat-file -p 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a > test.txt




  ~/Medium/github-repo-test on   main ⇡2 !1 ❯ git update-index --add --cacheinfo 100644 
  ~/Medium/github-repo-test on   main ⇡2 !1 ❯ git update-index --add --cacheinfo 100644
  ~/Medium/github-repo-test on   main ⇡2 !1 ❯ git update-index --add --cacheinfo 100644 83baae61804e65cc73a7201a7252750c76066a30 test.txt
❯ git update-index --add --cacheinfo 100644 83baae61804e65cc73a7201a7252750c76066a30 test.txt
❯ git status                
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)
                                                                               
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   test.txt                                     
                                                                               
Changes not staged for commit:                                  
  (use "git add/rm <file>..." to update what will be committed)                                                                                                
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        deleted:    test.txt                       
                                                                               
❯ git write-tree
1811a308a44c8ae9544af006839cc6bee665bc9c
❯ git cat-file -t 1811a3                           
tree                        
❯ git cat-file -p 1811a3
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob 83baae61804e65cc73a7201a7252750c76066a30    test.txt       
❯ git update-index --add --cacheinfo 100644 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a test.txt
❯ git status                
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)
                                                                               
Changes to be committed:                
  (use "git restore --staged <file>..." to unstage)       
        new file:   test.txt                                     
                                                                               
Changes not staged for commit:                                 
  (use "git add/rm <file>..." to update what will be committed) 
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md                                    
        deleted:    test.txt                                      
                                                                               
❯ echo "new file" > new.txt                                     
❯ git update-index --add new.txt                          
❯ git write-tree                                                 
def47b825cbfcf9682125311abf22a2ecae57417                          
❯ git cat-file -p def47b825cbfcf9682125311abf22a2ecae57417      
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md              
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt             
100644 blob fa49b077972391ad58037050f2a75f74e3671e92    new.txt                
100644 blob 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a    test.txt
❯ git cat-file -p def47b825cbfcf9682125311abf22a2ecae57417       
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md 
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob fa49b077972391ad58037050f2a75f74e3671e92    new.txt 
100644 blob 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a    test.txt
❯ git cat-file -p 1811a308a44c8ae9544af006839cc6bee665bc9c       
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md 
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob 83baae61804e65cc73a7201a7252750c76066a30    test.txt
❯                                                                              
❯                                                                              
❯                                                                              
❯ git cat-file -p def47b825cbfcf9682125311abf22a2ecae57417
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob fa49b077972391ad58037050f2a75f74e3671e92    new.txt
100644 blob 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a    test.txt
❯ git cat-file -p def47b825cbfcf9682125311abf22a2ecae57417
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob fa49b077972391ad58037050f2a75f74e3671e92    new.txt 
100644 blob 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a    test.txt   


❯ git cat-file -p def47b825cbfcf9682125311abf22a2ecae57417
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob fa49b077972391ad58037050f2a75f74e3671e92    new.txt
100644 blob 1f7a7a472abf3dd9643fd615f6da379c4acb3e3a    test.txt
❯ git cat-file -p 1811a308a44c8ae9544af006839cc6bee665bc9c
100644 blob ea5bfee17d5b29c27f181d2d0c8de801ae3aba89    README.md
100644 blob ed5a7803ae42fa34d3583cb3ecd8ed851b09a21b    file-1.txt
100644 blob 83baae61804e65cc73a7201a7252750c76066a30    test.txt
❯ git restore .                                           


```
