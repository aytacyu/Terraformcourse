## Datasources
It is possible to collect data and use in *tf* files : 
```
data "aws_availability_zones" "available" {}
resource .... {
...
availability_zone = data.aws_availability_zones.available.names[0]
...
availability_zones      = [data.aws_availability_zones.available.names]
```
## Terraform Graph
`terraform graph` : Visual graph for dependencies  
`apt install graphviz` & `terraform graph | dot -Tpng > graph.png` : create png file for visual dependency tree
## Output
to retrieve a value from for later usage:
```
output "pubip" {
    value = "${aws.instance.firstdemo.public.ip}"
}
```
to use output value : `terraform output pubip`
