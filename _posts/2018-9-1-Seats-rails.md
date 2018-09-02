---
layout: post
title:  "library seats"
date:   2018-09-01 14:00:00
categories: Linux, Rails, Ruby
tags: library
author: SteveDevin
mathjax: true
---
* content
{:toc}

 1. Install packages
     ```
     sudo apt-get update
     sudo apt-get install -y curl
     curl -sSL https://git.io/vVHhe | bash
     ```
     
     
     
     
         
 2. Install Nginx
     ``` 
     curl -sSL https://git.io/vVHhf | bash
     ```
     
 3. Install RVM & Ruby
    ```
     curl -sSL https://git.io/vVHhJ | bash
    ```
    Or use Ruby China mirror site for RubyGems and Ruby
    ```
     MIRROR=1 curl -sSL https://git.io/vVHhJ | bash
    ```
    
    run this to check
    ```
        ruby -v
        rvm -v 
    ```
    
 4. Install MongoDB
    ```
     curl -sSL https://git.io/vVHhT | bash
    ```
    
 5. Install Redis
    ```
     curl -sSL https://git.io/vVHhk | bash
    ```
    
 6. Install ElasticSearch
    ```
      curl -sSL https://git.io/vVHhm | bash
      sudo service elasticsearch status
    ```
    
 7. Install Docker
    ```
    curl -sSL https://git.io/vPypp | bash
    sudo docker info
    ``` 
    
 8. seats system
    ```
     git clone https://github.com/xxxx.xxxx.git
     cd library_xxxx/
     bundle install 
     apt-get install mysql-server
     rake db:create
     rake db:migrate
     whenever -i
     rails server
    ```
  
 9. [runing server](seats.idevin.cn)
