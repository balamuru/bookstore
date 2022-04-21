

## Generating Golang Server Stubs / API code 
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