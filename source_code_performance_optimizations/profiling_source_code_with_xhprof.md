# Profiling source code with XHProf

"In software engineering, profiling is a form of dynamic program analysis that measures, for example, the space (memory) or time complexity of a program, the usage of particular instructions, or the frequency and duration of function calls. Most commonly, profiling information serves to aid program optimization. Profiling is achieved by instrumenting either the program source code or its binary executable form using a tool called a profiler."[^1]

"XHProf is a hierarchical profiler for PHP. It reports function-level call counts and inclusive and exclusive metrics such as wall (elapsed) time, CPU time and memory usage. A function's profile can be broken down by callers or callees. The raw data collection component is implemented in C as a PHP Zend extension called xhprof. XHProf has a simple HTML based user interface (written in PHP). The browser based UI for viewing profiler results makes it easy to view results or to share results with peers. A callgraph image view is also supported."[^2]

After installing the XHProf PHP extension and a GUI[^3], we can easily identify the most CPU and memory hungry functions in plugins and themes. Then, we might either remove or begin to optimize them. Although there exist several WordPress profiling plugins such as Query Monitor or P3, they are not as exact and verbose as XHProf.

[^1]: Wikipedia: [Profiling (computer programming)](http://en.wikipedia.org/wiki/Profiling_%28computer_programming%29)

[^2]: Facebook: [XHProf Documentation — Web Archive](http://web.archive.org/web/20110514095512/http://mirror.facebook.net/facebook/xhprof/doc.html)

[^3]: Lamosty.com: [Profiling WordPress with xhprof on Mac OS X 10.10](https://lamosty.com/2015/03/profiling-wordpress-with-xhprof-on-mac-os-x-10-10/)