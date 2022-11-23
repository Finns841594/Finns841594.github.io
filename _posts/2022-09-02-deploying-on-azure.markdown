---
layout: post
title:  "Deploying My First Web On Azure"
date:   2022-09-02 20:00:00 +0200
categories: CS50
---

## 0

After finished the the problem set 9 "Finance" in CS50 course, I found this application for testing how good you can performance in stock market is worth sharing. So I decided to modify it and bring it online, so I can share this with my friends.

I encounterd several problems at the very first day. I will keep on updating this page for recording all the problems I meet, and all the solutions I found.

Here we go~

## 1. Hide the API_KEY

In the assignment, we need to register an API_KEY for checking the price of stocks at IEX. Everytime I run my finance program, I need to set the key as a environment variable(it takes me a while to get this). To not to modify the program too much, I find a way to set the environment variable in the program. But in this way, if I share my program online, for example on Github, all the people will see my API_KEY. I need to find a way to hide this.

## 2. Database

I decide to deploy this application on Azure servers from Microsoft. It is not so difficult to make it work, but here comes a problem about the database.

The database I used is SQLite, and it is part of the program which been uploaded with other files. I can register and trade successfully on the web, but I can not check the database like before, because there are no ways to access to the database file from the userside.


## 3. So many different versions of Python on my mac!

When I was following the tutorial on [Microsoft](https://docs.microsoft.com/zh-cn/azure/app-service/tutorial-python-postgresql-app?tabs=flask%2Cmac-linux%2Cvscode-aztools%2Cterminal-bash%2Cazure-portal-access%2Cvscode-aztools-deploy%2Cdeploy-instructions-azportal%2Cdeploy-instructions--zip-azcli%2Cdeploy-instructions-curl-bash), I found my mac did not excute the commend `pip install -r requirements.txt` right. 

- It returned `"/Users/yangfeng/Documents/CS50: bad interpreter: No such file or directory`,
- which is not the current directory `/Users/yangfeng/CS/msdocs-flask-postgresql-sample-app`.

Then I search on the internet, a answer leads me to check the version of Python. Here is what I got:
- Terminal: `which python` returns `/Users/yangfeng/opt/anaconda3/bin/python`, `python --version` returns `Python 3.8.8`;
- One of VSCode terminal: `which python` returns `/usr/bin/python`, `python --version` returns `Python 2.7.16`;
- Another VSCode terminal which I set virtual envrionment: `which python` returns `/Users/yangfeng/CS/msdocs-flask-postgresql-sample-app/.venv/bin/python`, `python --version` returns `Python 3.6.4`;

Have no idea......


## 4. Learning Postgresql

- Realized I can not use sqlite if I want to deploy my app on the Azure. So I got to learn the Postgrersql. It takes me a day to install, uninstall, and test to connect Postgrersql...

some useful commands

- start the server: brew services start postgresql
- stop the server: brew services stop postgresql
- restart: brew services restart postgresql

- its super wierd that if I create a table with name "tests", the cml will never return anything and the program will just being paused there.

- conn.commit() # 与sqlite不一样，用psycopg2操作postgres数据库，每次操作完都要commit一下才生效!


## 5. Psycopg2

- Psycopg2 is the library you use for connecting Postgresql database by python. The syntax, type of data that Psycopg2 returned are different from CS50 for Sqlite.

## 6. decimal in Python


## Jinja syntax note:

- To get the key and value from a dictionary that passed in, and use the key as the key for another dictionary:
    ```
        {% for k,v in dict1.items() %}
            <tr>
                <td class="text-start">{{ k }}</td>
                <td class="text-start">{{ dict2[k] }}</td>
                <td class="text-start">{{ v }}</td>
            </tr>
        {% endfor %}
    ```
