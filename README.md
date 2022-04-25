

## Generating Golang Server Stubs / API code 
The following instructions are a "somewhat more detailed" adaptation of instructions described in 

* Download swagger codegen (to ~/apps in this example)
* Execute the following to generate the golang server stub in the app directory
```
java -jar  ~/apps/swagger-codegen-3.0.34/modules/swagger-codegen-cli/target/swagger-codegen-cli.jar generate \
  -i bookstore.yaml \
  -l go-server \
  -o app
```
* `cd app`

## Execute the application
* Option 1: Execute the application directly
    * In `main.go` , fix the path to the `sw` import eg `sw "github.com/balamuru/bookstore/app/go"`
    * `go mod init`
    * `go mod tidy`
    * `go run main.go`
* Option 2: Build the application within Docker  
    * Build image  'docker build . -t bookstore' . In case this image is built on a machine behind a proxy, be sure to pass the proxies as command args `docker build  . -t bookstore --build-arg http_proxy --build-arg https_proxy`
    * Start container `docker run -it -p8080:8080 bookstore `  
## Access the stub API
* Use the appropriate client eg `curl -v http://localhost:8080/vgb/bookstore/1.0/shelves`

```
$ curl -v http://localhost:8080/vgb/bookstore/1.0/shelves
* About to connect() to localhost port 8080 (#0)
*   Trying ::1...
* Connected to localhost (::1) port 8080 (#0)
> GET /vgb/bookstore/1.0/shelves HTTP/1.1
> User-Agent: curl/7.29.0
> Host: localhost:8080
> Accept: */*
> 
< HTTP/1.1 200 OK
< Content-Type: application/json; charset=UTF-8
< Date: Mon, 25 Apr 2022 19:53:43 GMT
< Content-Length: 0
< 
* Connection #0 to host localhost left intact

```
