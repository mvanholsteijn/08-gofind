Go-Find Assignment
==================

Your task is to build a command line interface (CLI) tool to search files in a file hierarchy.
The tool will expect a location from where to start the search and some filters to prune the search tree.

Possible filters:
- -startswith name: return only the files that start with the given name.
- -ctime n: filter the files based on the creation time. The value n is given in minutes.
- -mtime n: filter the files bases on the modified time. The value n is given in minutes.
- -size n: filter the files bases on the size. The value n is given in Kb.
- -maxdepth levels: decent at most *levels* levels of directories bellow the root. The *levels* value must be a not-negative integer. The level 0 is considered the level of the root.

All the numerical filters can be positive or negative:
- +n - for values greater than n,
- -n - for values less than n,
-  n - for values equal with n
   The numerical filters can be supplied twice to search values inside a range [lower, upper]. The lower value must be positive and the upper value must be negative.


```sh
gofind [path] [filters]
```

Examples:

```sh
gofind ~/ -startswith python -> look for files that start with name 'python' in my home directory

gofind -startswith python -> look for files that start with name 'python' in my current working directory

gofind -ctime -60 -ctime +20 -> look for files that were created more then 20 minutes ago and less then 60 minutes ago

gofind -ctime -60 -size 30 -> files created less then 60 minutes ago with size bigger then 30 Kb

gofind -size -10 -maxdepth 3 -> files less then 10 Kb that are under 3 levels depth from current directory
```

When developing the code you should take into account software engineering practices. The solution must have automated tests and it should be distributed as a binary.
Don't forget to set up a CI/CD pipeline that lints, audits and tests your package!
numerical filters can be supplied twice to search values inside a range [lower, upper]. The lower value must be positive and the upper value must be negative.

Hints:
- fstest.MapFS is a great mock for testing
- table tests are great!

Optional:
- add an option to filter the name of the file using [glob pattern](https://en.wikipedia.org/wiki/Glob_(programming))
- add an option to filter the name of the file using regular expressions
- add the capability to use different units for time and size.
