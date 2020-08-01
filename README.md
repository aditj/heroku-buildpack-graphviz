Heroku Buildpack: Graphviz
===========================

Install [Graphviz](http://www.graphviz.org/) on Heroku.


Description
-----------

This buildpack installs the Graphviz binaries to `/app/graphviz/bin`. The used Graphviz version is:

* Graphviz 2.36.0 for stack Cedar-14
* Graphviz 2.20.2 for stack Cedar *(deprecated stack)*

The `/app/graphviz/bin` directory is added to the `PATH`. The variable `GRAPHVIZ_DOT` is set to `/app/graphviz/bin` (required by some tools, e.g. PlantUML).

The binaries are taken from the official Ubuntu packages: <http://packages.ubuntu.com/trusty/graphviz> for Cedar-14 (Ubuntu 14.04 LTS), and <http://packages.ubuntu.com/lucid/graphviz> for Cedar (Ubuntu 10.04 LTS).


Usage
-----

Simply do

~~~bash
heroku buildpack:set https://github.com/weibeld/heroku-buildpack-graphviz.git
~~~

On the next `git push heroku master`, the Graphviz buildpack will be used.

For more information on how to use custom buildpacks, see <https://devcenter.heroku.com/articles/third-party-buildpacks#using-a-custom-buildpack>.


Usage together with other buildpacks
------------------------------------

To use multiple buildpacks, you can use [heroku-buildpack-multi](
https://github.com/ddollar/heroku-buildpack-multi):

~~~bash
# Create file .buildpacks in app root, listing the buildpacks you want to use
cat <<EOF >.buildpacks
https://github.com/heroku/heroku-buildpack-ruby.git
https://github.com/weibeld/heroku-buildpack-graphviz.git
EOF

heroku buildpacks:set https://github.com/ddollar/heroku-buildpack-multi.git
~~~

On the next `git push heroku master`, all the buildpacks listed in `.buildpacks` will be used.


Verification
------------

You can verify the installation of Graphviz with

~~~bash
heroku run dot -V
~~~


License
-------

Licensed under the MIT License. See [LICENSE.md](LICENSE.md) file.

