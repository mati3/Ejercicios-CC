# [Microservicios](http://jj.github.io/CC/documentos/temas/Microservicios)

### 1º Ejercicio:

***Realizar una aplicación básica que use express para devolver alguna estructura de datos del modelo que se viene usando en el curso.***

![img](/img/Microservicios/ejer1_.png)

### 2º Ejercicio:

***Programar un microservicio en express (o el lenguaje y marco elegido) que incluya variables como en el caso anterior.***

![img](/img/Microservicios/ejer2_todos.png)

![img](/img/Microservicios/ejer2_todos_json.png)

![img](/img/Microservicios/ejer2_productoID.png)


### 3º Ejercicio:

***Crear pruebas para las diferentes rutas de la aplicación.***

Incluido en el archivo test_producto.rb para que me compruebe las rutas.

    def test_app_hola
        get '/'

        assert last_response.ok?
        assert_equal last_response.body, 'All responses are OK'
    end

    def test_app_id
        get '/producto/:id'

        assert last_response.ok?
        assert_equal last_response.body, 'All responses are OK'
    end

    def test_app_todos
        get '/todos'

        assert last_response.ok?
        assert_equal last_response.body, 'All responses are OK'
    end

### 4º Ejercicio:

***Experimentar con diferentes gestores de procesos y servidores web front-end para un microservicio que se haya hecho con antelación, por ejemplo en la sección anterior.***

Hemos elegido [foreman](https://github.com/ddollar/foreman) como administrador, necesitamos un archivo procfile, en este se llama al gestor de procesos web rackup que necesita un archivo config.ru donde poner los requerimientos de rack.

Config.ru:

        require './Catalogo/app_catalogo'

        run App

Procfile:

        web:rackup -p $PORT

### 5º Ejercicio:

***Usar rake, invoke o la herramienta equivalente en tu lenguaje de programación para programar diferentes tareas que se puedan lanzar fácilmente desde la línea de órdenes.***

Archivo rakefile:

    task default: %w[test]

      task :test do
            ruby 'Catalogo/tests/test_producto.rb'
      end

      task :build do
            sh "bundle install"
      end

      # en terminal: rake foreman env='cantidad'
      task :foreman do
        num = ENV['env']
        sh "foreman start -c web=#{num} "
      end

      task :client do
        sh "curl -v localhost:5000/todos"
      end