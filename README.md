# Log Analysis
An Udacity Full-Stack Web Development Nanodegree project created by Subhadeep Dey.

## About
It is a reporting tool that prints out reports (in plain text) based on the data in the database `news`. This reporting tool is a Python program using the `psycopg2` module to connect to the database.

The dataset has over 300k rows, and has to report the following questions:
1. What are the most popular three articles of all time?
2. Who are the most popular article authors of all time?
3. On which days did more than 1% of requests lead to errors?

The database `news` includes three tables:
1. `articles` - Includes information about the authors of articles.
2. `authors` - Includes the articles themselves.
3. `log` - Includes one entry for each time a user has accessed the site.

## Database Schema
**1. articles:**

| Column |           Type           |                       Modifiers                       | Storage  | Stats target | Description|
|--------|--------------------------|-------------------------------------------------------|----------|--------------|------------|
| author | integer                  | not null                                              | plain    |              |            |
| title  | text                     | not null                                              | extended |              |            |
| slug   | text                     | not null                                              | extended |              |            |
| lead   | text                     |                                                       | extended |              |            |
| body   | text                     |                                                       | extended |              |            |
| time   | timestamp with time zone | default now()                                         | plain    |              |            |
| id     | integer                  | not null default nextval('articles_id_seq'::regclass) | plain    |              |            |

Indexes:

   `"articles_pkey" PRIMARY KEY, btree (id)`    
   `"articles_slug_key" UNIQUE CONSTRAINT, btree (slug)`

Foreign-key constraints:  

   `"articles_author_fkey" FOREIGN KEY (author) REFERENCES authors(id)`
\
\
\
**2. authors:**

| Column |           Type           |                       Modifiers                       | Storage  | Stats target | Description|
|--------|--------------------------|-------------------------------------------------------|----------|--------------|-------------|
| author | integer                  | not null                                              | plain    |              |             |
| title  | text                     | not null                                              | extended |              |             |
| slug   | text                     | not null                                              | extended |              |             |
| lead   | text                     |                                                       | extended |              |             |
| body   | text                     |                                                       | extended |              |             |
| time   | timestamp with time zone | default now()                                         | plain    |              |             |
| id     | integer                  | not null default nextval('articles_id_seq'::regclass) | plain    |              |             |

Indexes:

   `"articles_pkey" PRIMARY KEY, btree (id)`    
   `"articles_slug_key" UNIQUE CONSTRAINT, btree (slug)`
    
Foreign-key constraints:

   `"articles_author_fkey" FOREIGN KEY (author) REFERENCES authors(id)`
\
\
\
**3. log:**
 
|  Column |           Type           |                    Modifiers                     | Storage  | Stats target | Description|
|-------|-------------------------|--------------------------------------------------|----------|--------------|-------------|
| path   | text                     |                                                  | extended |              |       |
| ip     | inet                     |                                                  | main     |              | |
| method | text                     |                                                  | extended |              | |
| status | text                     |                                                  | extended |              | |
| time   | timestamp with time zone | default now()                                    | plain    |              | |
| id     | integer                  | not null default nextval('log_id_seq'::regclass) | plain    |              | |


Indexes:

   `"log_pkey" PRIMARY KEY, btree (id)`
\
\
## Steps to run this project
1. Download and install Vagrant from [here](https://www.vagrantup.com/downloads.html).
2. Download and install VirtualBox from [here](https://www.virtualbox.org/wiki/Downloads).
3. Clone or download [this](https://github.com/udacity/fullstack-nanodegree-vm) repository.
4. Open the downloaded directory and navigate to the `vagrant/` directory.
5. Open terminal there, and type
                  
                  vagrant up
   This will cause Vagrant to download the Ubuntu operating system and install it. This may take quite a while depending on how fast your Internet connection is.
6. After the above command succeeds, connect to the VM by typing the following command:

                  vagrant ssh
           
6.  
