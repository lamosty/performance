# Techniques for Improving Website Loading Speed in General

Before we can delve into solutions to our problems, we need to list and describe several general techniques and measures used to improve not only the website loading times, but also a server resources usage and load.

## Web-Serving Software Efficiency

Using the most performant and the least resource-hungry web-serving software is usually the most effective way of improving web page loading speed. Some studies have found that even small changes to configuration files can a difference. In our work, we are making comparisons between the two most popular web-serving applications, namely Apache HTTP and Nginx, as well as comparisons between different PHP interpreters. Jump to section \ref{nginx-apache} for more details and statistics. 

## Server-Side Caching

Let us divide server-side caching into four main categories:

1. Caching intermediate PHP code
2. Caching the output of PHP interpreter (so called “page cache”)
3. Static resources (files) caching
4. Database caching

### 1. Caching intermediate PHP code

PHP source code is interpreted on each run, thus the PHP interpreter has to read and collect all required files each time a new request is sent to our WordPress-based website. With PHP \gls{opcode} caching, an intermediate source code is generated on the first run and stored temporarily. When a new request comes, instead of going through all the files, PHP loads cached opcode and executes it. We can observe the process from the figure 1.3.[^1]

![Figure 1.3: PHP execution diagram with and without APC opcode cache](../figures/php-opcode-caching.png)

[^1]inmotionhosting.com: [Speed up PHP with APC - Alternative PHP Cache](http://www.inmotionhosting.com/support/website/what-is/speed-up-php-with-apc)