configurator
=========
*it fetches configs*

## useage ##
Configurator accepts any number of paths that it will use to search for files (notice the trailing '/'). The paths are read in order until a config file is found. Once a file is found and read it will be cached.

```erlang
application:start(configurator).
configurator:add_path("/some/path/").
configurator:add_path("/other/path/").
configurator:config("secret_password.conf"). % -> [{password, "super secret"}]
```

if you need to review the paths available you can do the following:

```erlang
configurator:paths(). % -> ["/some/path/", "/other/path/"]
```

You can also manually add configurations

```erlang
configurator:set("some.conf", [{key, value}]).
configurator:config("some.conf"). % -> [{key, value}]
```

### config signature ###
config will return the parsed configuration, the atom not_found or the atom bad_config

## configuration format ##
all configs must be parseable by the [file:consult/0](http://www.erlang.org/doc/man/file.html#consult-1) function

