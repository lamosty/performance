# Techniques and Best Practices

## Autoloading PHP Classes

"Many developers writing object-oriented applications create one PHP source file per class definition. One of the biggest annoyances is having to write a long list of needed includes at the beginning of each script (one for each class)."[^1] Some programmers who are indifferent to the performance of their source code solve this problem by including all of the classes in one general file. The problem with this approach is that the classes which are not needed for a current code execution (for example requests to administration panel do not require classes used on the front-side of the website) are unnecessarily included every time a request is made, thus consuming more memory and CPU.

A proper solution is to make use of PHP's autoloading features. "You may define [...] a function which is automatically called in case you are trying to use a class/interface which hasn't been defined yet. By calling this function the scripting engine is given a last chance to load the class before PHP fails with an error."[^1]

## Time complexity of PHP functions

"In computer science, the time complexity of an algorithm quantifies the amount of time taken by an algorithm to run as a function of the length of the string representing the input. The time complexity of an algorithm is commonly expressed using big O notation, which excludes coefficients and lower order terms. [...] Time complexity is commonly estimated by counting the number of elementary operations performed by the algorithm, where an elementary operation takes a fixed amount of time to perform. Thus the amount of time taken and the number of elementary operations performed by the algorithm differ by at most a constant factor."[^2]

Using more efficient algorithms in plugins and themes, we might save tens to hundreds of milliseconds in our WordPress-based website execution time. Therefore, it is beneficial to have a basic knowledge of algorithms time complexity, especially the big O of native PHP functions.[^3]

## WordPress Plugin API

Plugin API, employed throughout the whole WordPress, makes it one of the most extensible PHP-based CMS. It is based on event-driven architecture (Observer design pattern), comprising hooks, actions and filters. "Hooks are provided by WordPress to allow your plugin to 'hook into' the rest of WordPress; that is, to call functions in your plugin at specific times, and thereby set your plugin in motion."[^4] Actions and filters are two kinds of hooks:

"**Actions** are triggered by specific events that take place in WordPress, such as publishing a post, changing themes, or displaying administration screen. An Action is a custom PHP function defined in your plugin (or theme) and hooked, i.e. set to respond, to some of these events."

"**Filters** are functions that WordPress passes data through, at certain points in execution, just before taking some action with the data (such as adding it to the database or sending it to the browser screen). Filters sit between the database and the browser (when WordPress is generating pages), and between the browser and the database (when WordPress is adding new posts and comments to the database); most input and output in WordPress passes through at least one filter. WordPress does some filtering by default, and your plugin can add its own filtering."

The performance optimizations of our website are based on utilizing proper action and filter hooks for our functions. To give you an example, when a plugin or a theme is activated (or deactivated), special action hooks are triggered. We should use them to initialize a plugin or a theme (e.g. create new user role, add rewrite rules — operations inserting data into database) instead of running these operations on each website execution (each request).

## WordPress database queries and structure

The database structure of a WordPress-based site is rather flexible, being able to accommodate various kinds of data. The "posts" table holds records of pages, posts and custom post types.[^5] Table "postmeta" can store additional information (metadata) for particular entries from the "posts" table. "term_taxonomy" table is used for data classification (categorization), holding terms from different taxonomies.[^6]

When adding data to posts, we can both add them as "postmeta" to a particular post, or create a new taxonomy with terms for the post. If we need to query the database by these additional data, it is better to add them as taxonomy with terms to obtain a greater querying performance. On the other hand, if the data are unique to a specific post and we do not generally need to query the database by it, it is better to add them as post's "postmeta" to save database disk space usage.[^7]

As far as querying data from a WordPress database is concerned, there are several principles we should follow to increase its performance:[^8]

- Use WP_Query class for database queries.
- Only run the queries that you need.
- Do not query all the posts at once — paginate them instead.

When working with specific data which do not fit into default WordPress tables (having worse performance or for logical reasons), it is better to create a custom table. In that case, we should use the method "prepare" of the "wpdb" class, automatically instantiated as "$wpdb" global variable to query these tables, as this method sanitizes user input, preventing SQL injection and other kinds of attacks.

[^1]: PHP.net: [PHP: Autoloading Classes - Manual](http://php.net/manual/en/language.oop5.autoload.php)

[^2]: Wikipedia: [Time complexity](http://en.wikipedia.org/wiki/Time_complexity)

[^3]: Stack Overflow: [performance - List of Big-O for PHP functions](http://stackoverflow.com/questions/2473989/list-of-big-o-for-php-functions)

[^4]: WordPress Codex: [Plugin API](https://codex.wordpress.org/Plugin_API)

[^5]: WordPress Codex: [Post Types](https://codex.wordpress.org/Post_Types)

[^6]: WordPress Codex: [Taxonomies](https://codex.wordpress.org/Taxonomies)

[^7]: OttoPress.com: [When to (not) use a Custom Taxonomy](http://ottopress.com/2011/when-to-not-use-a-custom-taxonomy/)

[^8]: 10up: [10up Engineering Best Practices](https://10up.github.io/Engineering-Best-Practices/php/)