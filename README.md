# angular-sendbox

If you need to rebuild image you can use `make build`. If you need to expose different ports or something.

You can create container like this:

docker stop angular-sendbox; docker rm angular-sendbox; docker create --name angular-sendbox -p 9000:9000 -p 35729:35729 -v $(pwd)/code:/home/yeoman/code bradojevic/angular-sendbox && docker start angular-sendbox

To execute and command:
  docker exec -it angular-sendbox bash

To scaffold angular project do:
  docker exec -it angular-sendbox yo cg-angular

In order for `serve` to work we need to change grunt config so you should have
`grunt.initConfig` updated to:
    connect: {
      main: {
        options: {
          port: 9000,
          hostname: '0.0.0.0',
          livereload: 35729
        }
      }
    },

docker exec -it angular-sendbox grunt serve
