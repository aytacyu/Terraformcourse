*Interactive prompting

variable "ami-type"{
}

*Passing through a file

variable "ami-type"{
default = "ami-92291j2k"
}

*Passing inline

terraform apply -var amitype="ami-9212323"


Note: file extension should be .tf


*Map example1

in main.tf:
instance_type="${lookup(var.instance_type,var.env)}"

in variables.tf:
variable "env" {}
variable "instance_type" {
	type = "map"
	default = {
		dev = "t2.micro"
		test = "t2.medium"
	}
}

*Map example2

in main.tf:
instance_type="${lookup(var.ami_type,var.region)}"

in variables.tf:
variable "region" {
	default = "us-east-2"
}
variable "ami_type" {
	default={
		type="map"
		us-east-1="ami-14c5486b"
		us-east-2="ami-922914f7"
	}
}

*List example

variable "sgs" {
	type = "list"
	default = ["sg-07b2fc6c", "sg-48bba323"]
}

