# About WordPress

## General Information

Citing WordPress.org, "WordPress is web software you can use to create a beautiful website or blog."[^1] Simply put, WordPress is a powerful, open-source web publishing software, content management system and a web platform for building rich web applications. People and companies use WordPress for various purposes and reasons, most notably for their blogs, websites, e-commerce solutions and large web portals. At the time of writing, it is estimated that about 24%[^2] of all websites, whose content management system is known, are being run on WordPress. This number is rather astonishing because it means that visiting five random websites, one of them will be a WordPress-powered one.

WordPress, in comparison to other web software and frameworks, is a full-featured, stand-alone web publishing software and content management system. WordPress is written mostly in PHP language, accompanied with JavaScript scripts and CSS stylesheets. At its core, it consists of a request-response routing subsystem, classes for managing database and content, security features and others. Initially, WordPress was started as an open-source hobby project of Matt Mullenweg in 2003[^3]. Since then, web programmers from all around the world have contributed to it, making it robust, secure and fast. However, as there are several bottlenecks in the system, we, web developers, decided to analyze and improve them. Our findings and results are summarized in this thesis.

## WordPress-based Website

In order to customize the look and feel of user’s instance of the website, there exists a mechanism called the WordPress Theme. A WordPress theme is simply a collection of scripts, stylesheets and images which get combined, processed and the generated content is sent back to the client. A user can install any theme which is compatible with his or her WordPress version. There is no central body governing the quality and correctness of a theme. As theme developers are free to build them almost arbitrarily, numerous security and performance flaws occur. The WordPress Plugin is a pluggable piece of software which enhances the basic WordPress functionality, thus enabling its users to heavily modify their WordPress-based web applications and sites. Plugins are also open source and without any quality guarantees, therefore experiencing the same problems as the aforementioned themes. 

Moreover, when a user has a high-traffic website, his web delivering server is not able to keep up with all the requests resulting in a slow, unresponsive website. The reader might assume that the problems would be solved by increasing plugins quality. While the previous statement is true, it is usually not viable, mainly due to a reason that work of an experienced web developer is relatively expensive. In many cases, upgrading the server and/or getting additional one(s) is the preferred way. In our work, we are concerned with optimizing the server software first and only then examining the best practices, tips and tricks of a plugin or a theme development.

[^1]WordPress.org: [Blog Tool, Publishing Platform, and CMS](https://wordpress.org/)

[^2]W3Techs.com: [Usage statistics and market share of WordPress for websites](http://w3techs.com/technologies/details/cm-wordpress/all/all)

[^3]WordPress Codex: [History](http://codex.wordpress.org/History)