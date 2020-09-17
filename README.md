# Terraform provider vscale

[![Github Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://github.com/burkostya/terraform-provider-vscale)


# Build from source!
Create folders
  - mkdir -p $GOPATH/src/github.com/terraform-providers;
  - cd $GOPATH/src/github.com/terraform-providers
  - gir clone https://github.com/burkostya/terraform-provider-vscale.git

  #### Important . Change owner !!
  ```sh sudo chown -R root:root ./go ```

  ### Before buildin, install GO and setup PATH.
```sh
export GOROOT=/usr/local/go/
export GOPATH=$HOME/work
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
  ```
  ##  Building module
 ``` go mod init terraform-provider-vsacle ```

 ```go mod vendor ```

Create the appropriate subdirectory within the user plugins directory for the Vscale provider.  Substitute [OS_ARCH] with your current OS Architecture. You can find a full list of supported GO_ARCH

   ``` ~/.terraform.d/plugins/vscale.com/edu/vscale/0.1/linux_amd64  ```

 Finally, build the binary and move it into your user Terraform plugins directory. This allows you to sideload and test your custom providers.

``` go build -o terraform-provider-vscale  ```

  Then, move the binary to the appropriate subdirectory within your user plugins directory, replacing [OS_ARCH] with your system's OS_ARCH.

  ``` mv terraform-provider-vscale ~/.terraform.d/plugins/vscale.com/edu/vscale/0.1/linux_amd64 ```

  ### Initialize workspace
Add the following to your main.tf  file. This is required for Terraform 0.13+.
 ``` sh
  terraform {
  required_providers {
    vscale = {
      versions = "0.1"
      source = "vscale.com/edu/vscale"
    }
  }
}
 ```
Then, initialize your Terraform workspace. If your Hashicups provider is located in the correct directory, it should successfully initialize.  
Otherwise, move your Vscale provider to the correct directory:
>> ~/.terraform.d/plugins/${name}/${version}/${os}_${arch} "example"
~/.terraform.d/plugins/vscale.com/edu/vscale/0.1/linux_amd64  "my directory"

 ```sh
 terraform init
 ```
