# Introduction
Nothing here at the moment

# Request
### Discovery
* Type in the following commands
```REST
OPTIONS http://restful.dev/wp-json/wp/v2.posts
```
* You will see all the available commands

### Resource
Something more coming after

# Response
### HEAD
* see the following codes
``` REST
HEAD http://restful.dev/wp-json/wp/v2/posts
```
### DELTE
* When successful, the status of a post is changed from "public" to "trash"
* If you want to force the post to be deleted exactly, here is the code
```REST
DEETE http://restful.dev/wp-json/wp/v2/posts/15?force=true
```
 Also note that this is dependent on the methods, usually you need to use `OPTIONS` to look up all
 the methods available from a resource
