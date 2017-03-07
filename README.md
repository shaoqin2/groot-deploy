#Groot Deployment 

###Deploying Groot is now really easy

Prerequisites:
- Have an [ssh key attached to your GitHub](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).

1. Install repo - https://android.googlesource.com/tools/repo/

    Mac OS
    ```sh
    brew install repo 
    ```

    Ubuntu 14.04+
    ```sh    
    sudo apt install repo

    ```
2. Clone this repository
    ```sh
    git clone https://github.com/acm-uiuc/groot-deploy
    ```
    
3. Within this directory run the following command to start managing the projects

    ```sh    
    cd groot-deploy
    repo init -u git@github.com:acm-uiuc/groot-manifest
    ```
    
4. Run the following command to grab the latest releases of all repositories

    ```sh    
    repo sync
    ```

    - If you want to update changes with the latest code just run it again.

# First Time Setup
- Golang 
    + Install Software 
    ```sh
    mkdir [SOME DIRECTORY]
    mkdir [SOME DIRECTORY]/bin && mkdir [SOME DIRECTORY]/lib \
    && mkdir [SOME DIRECTORY]/src
    mkdir -p [SOME DIRECTORY]/src/github.com/acm-uiuc
    ```
    --- Add to (.zshrc/.bashrc) ---
    ```sh
    export GOPATH=[SOME DIRECTORY]

    #macOS 
    export GOROOT=/usr/local/opt/go/libexec
    #Ubuntu 14.04+
    export GOROOT=/usr/local/go

    export PATH=$PATH:$GOPATH/bin
    export PATH=$PATH:$GOROOT/bin
    ```
    ```sh
    # macOS
    brew install go
    # Ubuntu 14.04+
    sudo curl -O https://storage.googleapis.com/golang/go1.7.linux-amd64.tar.gz
    sudo tar -xvf go1.7.linux-amd64.tar.gz
    sudo mv go /usr/local
    ```
    + Add ```groot``` to ```GOPATH```
    ```sh 
    ln -s [PATH to groot-deploy]/groot [SOME DIRECTORY]/src/github.com/acm-uiuc/groot
    ``` 
- Node
    + Install Software
    ```sh
    # macOS
    brew install node
    # Ubuntu 14.04+  
    sudo apt-get install nodejs
    sudo apt-get install npm
    sudo apt-get install build-essential
    sudo apt-get update
    sudo apt-get install build-essential libssl-dev
    curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.31.0/install.sh -o install_nvm.sh
    bash install_nvm.sh
    source ~/.profile
    nvm install 7.2.0
    nvm use 7.2.0
    ```
- Ruby
    + Install Software
    ```sh
    # macOS
    brew install rbenv
    # Ubuntu 14.04+
    sudo apt-get install autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm3 libgdbm-dev
    git clone https://github.com/rbenv/rbenv.git ~/.rbenv
    
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc
    source ~/.bashrc
    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build

    rbenv install 2.3.1
    rbenv global 2.3.1
    # You may have to restart your terminal session
    gem install bundler
    ```
- Python 
    + Install Software
    ```
    # macOS 
    brew install python 
    # Ubuntu
    sudo apt install python-pip
    ```
    
- MySQL
    + Install Software
    ```sh
    #macOS
    brew install mysql
    mysqladmin -u root password '' 
    mysql.server restart
    # Ubuntu 14.04+
    sudo apt-get install mysql-server
    sudo apt-get install libmysqlclient-dev
    sudo mysqld --intialize
    ```

    Run the MySQL script to ensure that all databases from all services have been created.

# Running the Server 
- Run the ```dev_spinup.sh``` script to start up a dev instance of groot (will grab the latest version of each service on github)
- Run the ```prod_spinup.sh``` script to start a production version of Groot (will set appropriate environment variables and expect the API keys to be set correctly)

## License

This project is licensed under the University of Illinois/NCSA Open Source License. For a full copy of this license take a look at the LICENSE file. 

When contributing new files to this project, preappend the following header to the file as a comment: 

```
Copyright © 2017, ACM@UIUC

This file is part of the Groot Project.  
 
The Groot Project is open source software, released under the University of Illinois/NCSA Open Source License. 
You should have received a copy of this license in a file with the distribution.
```
