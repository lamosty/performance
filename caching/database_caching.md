# Database Caching

WordPress was programmed with the support of database caching in mind. Core functions and methods querying the database (such as `get_option`, `get_posts` and others) use WordPress Object Cache API[^1] on the background. 

The default Object Cache API caches the database queries and results in a PHP array — only for a duration of the script execution (one request). On one hand, this mechanism is useful in templates, where the same information about the site is retrieved multiple times (for example `get_bloginfo` function). On the other hand, when many users visiting our site request the same page, the same database queries have to be made unnecessarily multiple times.

If we need to store the database cache persistently, we can use an in-memory database. "An in-memory database is a database management system that primarily relies on main memory for computer data storage. It is contrasted with database management systems that employ a disk storage mechanism. Main memory databases are faster than disk-optimized databases since the internal optimization algorithms are simpler and execute fewer CPU instructions. Accessing data in memory eliminates seek time when querying the data, which provides faster and more predictable performance than disk."[^2]

The two most popular in-memory databases in the WordPress ecosystem are Memcached and Redis. In our work, we have chosen to use Redis as it is modern, well-supported and having all the features of Memcached.[^3] In order for WordPress Object Cache API to use Redis for database caching, we need to install Redis server and Redis PHP connector (driver). We have prepared an Ansible playbook which downloads a PHP driver for Redis and installs it into the currently installed WordPress site (whether basic or advanced). Within your command line, navigate to the wordpress-ansible directory and run the "wordpress_redis_db_cache.yml" Ansible playbook:

```
ansible-playbook -i hosts wordpress_redis_db_cache.yml
```

Analogous to how we benchmarked the web-serving software in the previous chapter, we configured a Loader.io test and performed several load tests for the site with Redis database caching enabled. Suprisingly, resulting charts did not show any noticeable improvements[^4] over the other tests. Contemplating over this issue, we think that the database on our testing server is not a bottleneck. However, as this has not been proved yet, it might be a subject of a future work.

[^1]: WordPress Codex: [Class Reference/WP Object Cache](https://codex.wordpress.org/Class_Reference/WP_Object_Cache)

[^2]: Wikipedia: [In-memory database](http://en.wikipedia.org/wiki/In-memory_database)

[^3]: Stack Overflow: [caching - Memcached vs. Redis?](http://stackoverflow.com/questions/10558465/memcached-vs-redis)

[^4]: Loader.io: [Nginx HHVM Redis DB caching: A load test by loader.io](http://ldr.io/1cbcY7Y)