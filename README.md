# Resources

Deploy Go Lambda functions with container images
`https://docs.aws.amazon.com/lambda/latest/dg/go-image.html`

Handler function example
`https://docs.aws.amazon.com/lambda/latest/dg/golang-handler.html`

## Upload lambda using container image

1. Create project folder and run `go mod init github.com/anitabee/hello-go-lambda`
2. Create handler function from above example
3. Run `go mod tidy`
4. `docker build -f Dockerfile -t hello-world .`
5. Create ECR repository and use push command instructions to deploy over aws cli
6. Create AWS Lambda function selecting Container image option and select uploaded ECR repository
7. Create test using:
    ```json
        {
            "name": "MyName"
        }
    ```

## Upload lambda using native GO

1. Prepare zip file containing go binary:

```bash
go mod tidy 
GOOS=linux go build main.go
zip function.zip main
```

2. Create function selecting Author from scratch option and select GO 1.x runtime
3. Upload zip file from first step
4. Create test using:
    ```json
        {
            "name": "MyName"
        }
    ```
