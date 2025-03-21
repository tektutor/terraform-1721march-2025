## Info - Ansible Automation Platform
<pre>
- was also called as Ansible Tower
- it is developed on top the AWX (open source)
- AWX is developed on top Ansible core (open source)
- unlike Ansible core, Ansible automation platform supports webconsole, user management, etc.,
- this is a Red Hat Enterprise product with world-wide support
- functionally AWX and Ansible Automation Platform are one and same
- it is not possible develop Ansible Playbook within AWX or Ansible Automation Platform
- hence, we still need Ansible core to develop playbooks and test them before we push it to GitHub or any version control
- the existing Ansible Playbooks we can execute via Ansible Automation Platform
- can be installed as a stand-alone application on any Linux Distributions or we can install inside Kubernetes or Openshift
</pre>

## Lab - Starting Minikube to use Ansible Tower
```
minikube status
minikube start
minikube status
kubectl get nodes
```

Expected output
![image](https://github.com/user-attachments/assets/310342c7-b2e8-4edd-aa4e-3d5b15fb60ea)
![image](https://github.com/user-attachments/assets/befcda35-93a5-4a92-ab74-8773102bc9d5)

Launching AWX - opensource Ansible Automation Platform
```
minikube service awx-demo-service --url -n ansible-awx
```

You can launch the AWX webconsole using the url shown by the above command in the Ubuntu RPS cloud machine
<pre>
http://192.168.49.2:31225
</pre>
![image](https://github.com/user-attachments/assets/70d5fb5d-62fb-4321-b5c4-e5c2792b0c51)


To retrieve the AWX password ( save the password in a file to avoid typing this lengthy command each time )
```
kubectl get secret awx-demo-admin-password -o jsonpath="{.data.password}" -n ansible-awx | base64 --decode; echo
```

Login credentials for AWX is
<pre>
username - admin
password - 
</pre>
![image](https://github.com/user-attachments/assets/910b3144-e59c-459a-8c5b-26788553153c)
![image](https://github.com/user-attachments/assets/fb6b39b7-9752-4ce6-83b7-45ba185e7afa)
![image](https://github.com/user-attachments/assets/06607ea3-0fbf-4dfa-8cd4-0f4e78af0221)


## Lab - Creating a Project in Ansible Automation Platform
Navigate to your Ansible Automation Platform Dashboard page
![image](https://github.com/user-attachments/assets/23c4d27e-190c-49a5-9b82-29956b572b87)

Under Resources menu, select "Projects"
![image](https://github.com/user-attachments/assets/9025034d-15fe-4b68-9e4c-bfe5ffd0b3c7)
Click "Add" to create a new project
![image](https://github.com/user-attachments/assets/654db108-2a5e-4d39-a5fc-112fc58c5839)
Select "Git"
![image](https://github.com/user-attachments/assets/35e47d0e-05dc-43e0-a1c1-8c2d2c99c829)
![image](https://github.com/user-attachments/assets/25ce7682-a2f5-4424-96ac-8142a4929bb2)
![image](https://github.com/user-attachments/assets/8e51cd5c-3360-4fcd-8d41-941018d2cc2e)
Click "Save"
![image](https://github.com/user-attachments/assets/8d4c187b-8e21-4502-812b-1280be1cc3de)
![image](https://github.com/user-attachments/assets/104e7328-4198-4c22-9a9d-1eeb2b4e1b9b)
![image](https://github.com/user-attachments/assets/705c3006-183a-43dc-a455-1953a159a6fd)
![image](https://github.com/user-attachments/assets/31880195-ed4a-431a-adce-20d9b2460cae)
![image](https://github.com/user-attachments/assets/2f9f42f3-ff4c-455a-ba9c-4aa2c2bce3f3)
![image](https://github.com/user-attachments/assets/85e9b257-048c-4dea-ad77-302d6e9ecc8a)

## Lab - Creating an Inventory in Ansible Automation Platform
Navigate to your Ansible Automation Platform Dashboard page
![image](https://github.com/user-attachments/assets/23c4d27e-190c-49a5-9b82-29956b572b87)

Under Resources menu, select "Inventories"
![image](https://github.com/user-attachments/assets/b19a8acf-a079-4dd6-a387-d1a6c69589a5)
Click "Add" to create an Inventory
![image](https://github.com/user-attachments/assets/232c3bd3-617c-4908-96cf-538bd3cf81c2)
Select "Add Inventory"
![image](https://github.com/user-attachments/assets/b2361f4e-ccf9-438f-ba4e-235dbb5bee7c)
![image](https://github.com/user-attachments/assets/6c8c0acd-bdce-45c9-b9cb-a8654aaa72d3)
Give a name for your inventory
![image](https://github.com/user-attachments/assets/f51cddfa-d894-46ac-86ef-c8e9d8d65744)
Click "Save" button
![image](https://github.com/user-attachments/assets/d36f49d0-6e30-499e-855d-d11ec2ad4eec)

Click "Hosts" Tab within the inventory you created
![image](https://github.com/user-attachments/assets/5e2517ac-c132-4d6b-a650-3d81e594428e)

Find your Lab machine IP address
![image](https://github.com/user-attachments/assets/a4f246b8-52be-4dac-a782-1fb3d048cce6)

Click "Add" to add a Host(Ansible node connection details)
![image](https://github.com/user-attachments/assets/9c4e47b5-8f24-49b7-9340-817f54ddc133)
![image](https://github.com/user-attachments/assets/1f08e35a-24fc-47a1-a3c3-594d7a76f88b)
Click "Save"

Click "myinventory", "hosts" 
![image](https://github.com/user-attachments/assets/127a846a-fca6-46a1-8db8-47bdfc9f61e6)
![image](https://github.com/user-attachments/assets/a68e73e4-8023-4465-a5f8-0bccc03ae056)
![image](https://github.com/user-attachments/assets/9919d434-f54d-435b-9631-20500c712663)
![image](https://github.com/user-attachments/assets/ca5f6d2c-ba8f-46bf-8ae4-bc0a776ecfb2)
![image](https://github.com/user-attachments/assets/e8abf058-fa5a-4394-92b1-823609d81be8)
![image](https://github.com/user-attachments/assets/7a3f3d56-30d2-432c-b5ef-9bd6e88b1785)
![image](https://github.com/user-attachments/assets/b989c1ad-c146-4df4-80e1-53e2c240843a)
![image](https://github.com/user-attachments/assets/d7ba0b8d-5800-429b-acf1-eb13b5a283e5)
![image](https://github.com/user-attachments/assets/5493ce9a-35d6-420f-8452-7e5240ce7be0)


## Lab - Create Credentials
Navigate to your Ansible Automation Platform Dashboard page
![image](https://github.com/user-attachments/assets/23c4d27e-190c-49a5-9b82-29956b572b87)

Under "Resources" menu, select "Credentials"
![image](https://github.com/user-attachments/assets/9782831f-630c-4796-9402-b83be9cc87ab)
Click "Add" to create credentials
![image](https://github.com/user-attachments/assets/e66ba643-569f-4020-9937-1f056a00d5d6)
![image](https://github.com/user-attachments/assets/6d5e84af-db22-4352-9134-9135efee0051)
![image](https://github.com/user-attachments/assets/0de5c301-e28c-4453-8710-562cbce95d3a)
![image](https://github.com/user-attachments/assets/045f6044-589d-49eb-8c62-f2831d6e7085)
![image](https://github.com/user-attachments/assets/26d32cf0-60bd-403b-8681-bc1552f70796)
![image](https://github.com/user-attachments/assets/7727ee41-de92-42a0-91d2-69ad8aca42eb)
![image](https://github.com/user-attachments/assets/eb730661-8bf3-4bf9-80e8-fe8cc10a0445)
Click "Save"
![image](https://github.com/user-attachments/assets/e279adc4-fd37-4a9e-be84-52183cc1b949)
![image](https://github.com/user-attachments/assets/5e6d4122-da26-4756-a075-de4b58b3444f)



##

Click "Run command"
![image](https://github.com/user-attachments/assets/d2f1c793-0c2e-4a63-b70c-d7ee3ab26c0a)
![image](https://github.com/user-attachments/assets/e818aa76-00f7-41a0-970a-239d8d7ce54d)
Choose a module, select ping
![image](https://github.com/user-attachments/assets/2edbe0ba-e718-4320-b01d-d6da89c7320f)
![image](https://github.com/user-attachments/assets/8b0683ea-b355-4637-9515-f8b05be84a56)
Click "Next"
![image](https://github.com/user-attachments/assets/29f7c5e4-080e-4139-81b0-8f798fcd90c8)
Click "Next"
![image](https://github.com/user-attachments/assets/421b7806-319d-494f-be58-ab32164299aa)
![image](https://github.com/user-attachments/assets/a53735eb-a99d-4eaa-81ec-fdd953241e98)
![image](https://github.com/user-attachments/assets/d72dc32d-e518-4404-b1a3-ab94ac28e1ef)
Click "Launch"
![image](https://github.com/user-attachments/assets/35459970-67de-42c0-a049-5985fbaaab97)
![image](https://github.com/user-attachments/assets/5dcd6fa0-78fb-45cc-abbb-8c6f10f1c751)

## Lab - Creating a Job Template to invoke Ansible Playbook
Navigate to your Ansible Automation Platform Dashboard page
![image](https://github.com/user-attachments/assets/256e8757-4e9b-4cb2-b8ab-8343e2a73dd1)

On the Resources menu, click "Templates" to create a Job Template 
![image](https://github.com/user-attachments/assets/48e06b81-27ad-4121-bdb4-0b00a3dd3ccc)

Click "Add"
![image](https://github.com/user-attachments/assets/31f8b13f-c94c-4856-bcd2-caf79c79519d)
Select "Add Job Template"
![image](https://github.com/user-attachments/assets/ef9ee9da-02fb-4279-93f1-fdf50d9810f6)

![image](https://github.com/user-attachments/assets/b7ff8578-0ee8-4420-b5fc-2b7ef5474f52)
![image](https://github.com/user-attachments/assets/c2a7146f-6c29-4bb6-91d8-94f66c625559)
![image](https://github.com/user-attachments/assets/8852d272-b637-4cc9-89b5-d86cdc61dd21)
![image](https://github.com/user-attachments/assets/888939f8-d351-475f-a51a-f725d0f6a6aa)
![image](https://github.com/user-attachments/assets/8f5b0334-1bf5-4690-8577-b589904c9147)
![image](https://github.com/user-attachments/assets/977dda8c-1496-4a16-b89f-56d17e58130f)
![image](https://github.com/user-attachments/assets/f4438d57-2cc0-4d7b-bea3-cdde67b4359f)

![image](https://github.com/user-attachments/assets/d33159ef-1eb6-475e-9858-77a5ccc9a3ca)
Click "Save"
![image](https://github.com/user-attachments/assets/739330d0-717a-4ad6-9d08-a1281b3b69a2)
![image](https://github.com/user-attachments/assets/a7ef8b36-9a94-4156-8246-0773bce3d1ac)
Click "Launch" to run the playbook

![image](https://github.com/user-attachments/assets/b2793f94-4872-4184-8706-64f181711bf1)

![image](https://github.com/user-attachments/assets/098bf9d1-77b5-4724-bd7a-0aeddff6f977)

![image](https://github.com/user-attachments/assets/f940905f-5bb8-4f3d-868e-fe3d59373adb)


## Lab - Create a normal user
![image](https://github.com/user-attachments/assets/79f13f3a-12ed-4486-a525-1d84243b7d02)


## Lab - Installing tower cli
```
sudo apt install -y python3-pip
pip install ansible-tower-cli --break-system-packages
```
![image](https://github.com/user-attachments/assets/d18ad3b7-010a-4762-baed-42ffb4f40c2f)
![image](https://github.com/user-attachments/assets/1b3a19c8-3b76-47fd-90eb-d34e454c4574)
![image](https://github.com/user-attachments/assets/0b090ba2-dd13-4f14-b332-9d2bdac2da0c)


## Lab - Using tower-cli
```
export PATH=$PATH:/home/rps/.local/bin
tower-cli config host http://192.168.49.2:31225
tower-cli config username admin
tower-cli config password your-admin-password
tower-cli config verify_ssl false
tower-cli project list
tower-cli job list
tower-cli job launch --job-template=9
```

## Demo - Installing Visual Studio Code in Lab machine
```
sudo snap install code --classic
```

## Info - Go Programming Language Overview
<pre>
- is a programming language developed in C by Google
- later the go lang is recompiled/redeveloped in Go lang
- syntax wise, it is more or less similar to C Programming language
- also called as Golang
- golang design philosophy is to
  - keep it simple, hence it supports a total of just 25 keywords
  - loops - only for loop is supported
  - there are no class, only struct is supported to define user-defined data-type
  - supports pointers but manages memory using garbage collector
- golang supports the below basic data-types
  - bool
  - string
  - int, int8, int16, int32 and int64
  - uint, unit8, uint16, uint32, uintptr
  - byte ( alias of uint8 )
  - float32, float64( equivalent to double in most programming languages )
  - complex64, complex128
- it is a statically typed programming language
  - meaning, every variable must be declared before using it
- strongly typed
  - once a variable is declared as int, it will remain as integer throught the life-time of the application
- golang supports garbage collection
- some of the tools developed in golang
  - can be used to develop normal desktop applications, system utilities, compilers, interpreters, web application, AI 
  - Docker, Kubernetes, OpenShift, Terraform, DropBox, etc.,
- it is faster than most compiled languages
  - faster than .Net, Java, etc.,
  - equivalent to C/C++ in terms of performance
- Editor recommended to develop golang is Microsoft's Visual Studio code
- Vim editor also works fine if you are comfortable 
</pre>

## Lab - Checking if go is installed in your lab machine
```
go version
```

Expected output
![image](https://github.com/user-attachments/assets/638a308f-8af1-4697-994f-ecbc03ff46d7)

## Lab - Writing your first Hello World application in Golang

Create a file named hello.go with the below content

<pre>
package main

import "fmt"

func main() {
  fmt.Println ( "Hello World !" )
}
</pre>
Note
<pre>
- fmt package has input/output functions like Print, Println, Print, Sprint, Sprintf, Sprintln, Fprint, Fprintf, Fprintln, Scan,Scanf, Scanln, Sscan, Sscanln, Fscan, Fscanf, Fscanln, Errorf, etc.,
- main is the entry point function, i.e the first function that will be invoked automatically by golang when you run the above program.
- the begining curly bracket must be in the same line where main() is defined, if you bring it to next line, go compiler will report a compilation error
</pre>

Run the program
```
go run ./hello.go
```

Expected output
![image](https://github.com/user-attachments/assets/8fc7d876-2893-45a0-855a-c779c527caeb)

## Lab - Golang loop

Create file named loops.go with the below content
<pre>
package main

import "fmt"

func main() {

	count := 5 //Declares a count variable of type int and assigns a value 5

	for count > 0 {

		fmt.Println(count)
		count-- //equivalent to count = count - 1
		//--count pre-decrement is not supported in golang
		//++count pre-increment is not supported in golang
		//count++ is supported in golang
	}

	fmt.Println("Value of count is", count, " after for loop")

	count = 0 //Variable is already declared in line no 7, we are reinitializing count with 0

	for count = 1; count < 10; count++ {
		fmt.Printf("%d\t", count)
	}

	fmt.Println()
}  
</pre>

Note
<pre>
- In the above code at line number 3, we are trying to import a packaged called fmt
- the fmt package has input/output functions like Print, Println, Printf, ScanF, etc.,
- In order to use any functions from package fmt, we must first import it
</pre>


You can run the application as shown below
```
go run ./loops.go
```
Expected output
![image](https://github.com/user-attachments/assets/554f1e7c-072b-4365-98e3-fbf8fc3e2753)
![image](https://github.com/user-attachments/assets/899c6331-d298-425b-bfad-8619661d3408)

## Lab - Switch case

Create a file named switch-case.go with the below content
<pre>
package main

import "fmt"

func main() {

	var direction string //declares a variable named direction of type string

	//Valid values are east, west, north, south
	fmt.Print("Enter some direction :")
	fmt.Scanln(&direction)

	switch direction {
	case "east":
		fmt.Println("You entered direction ", direction)
	case "west":
		fmt.Println("You entered direction ", direction)
	case "north":
		fmt.Println("You entered direction ", direction)
	case "south":
		fmt.Println("You entered direction ", direction)
	default:
		fmt.Println("Invalid direction, possible values are east, west,north,south")
	}
}	
</pre>

Run it
```
go run ./switch-case.go
```

Expected output
![image](https://github.com/user-attachments/assets/088a54df-4c31-4bc7-9014-f392bb5a396e)
![image](https://github.com/user-attachments/assets/987edab4-59bb-4b38-b40b-03abb3d5e4a1)

## Lab - Array

Create a file named arrays.go with the below content
<pre>
package main

import "fmt"

func main() {

	//We have declared an array of integers of size 5
	//So we can store upto 5 integer values into this array
	//golang array size is fixed
	//array index starts from 0
	//array index range is 0 to 4, total 5 values
	var arr[5] int

	//let's assign some values into the array
	arr[0] = 10
	arr[1] = 20
	arr[2] = 30
	arr[3] = 40
	arr[4] = 50

	//arr[5] = 60 This will report array index out of bounds error

	fmt.Println( "Array elements are ...")
	fmt.Println(arr)

	count := len(arr)
	fmt.Println("Length of array :", count )

	//Modifying values stored in an array
	arr[3] = 25

	fmt.Println("Array elements are ...")
	for i := 0; i < count; i++ {
		fmt.Printf("%d\t", arr[i] )
	}
	fmt.Println()
}	
</pre>


Run the application
```
go run ./arrays.go
```
Expected output
![image](https://github.com/user-attachments/assets/4563b63f-1e1a-4cff-abd1-4027c44b6bfd)

## Lab - If else

Create a file named if-else.go with the below code
<pre>
package main

import "fmt"

func main() {

	if 8%2 == 0 {
		fmt.Println("8 is even number ")
	} else {
		fmt.Println("8 is an odd number")
	}

}
</pre>

Run the program
```
go run ./if-else.go
```

Expected output
![image](https://github.com/user-attachments/assets/3eb732d3-5a70-4afe-a711-c7e49a0eeeaf)

## Lab - Golang functions with parameters

Create a file named function.go with below code
<pre>
package main

import "fmt"

func main() {

	fmt.Println(sayHello("Golang"))

}

// This function accepts a string input and returns a string value
func sayHello(msg string) string {
	return "Hello " + msg + " !"
}	
</pre>

Run it
```
go run ./function.go
```

Expected output
![image](https://github.com/user-attachments/assets/3560eb04-5485-432c-b4ea-5e338823cdb2)

## Lab - Function with multiple returns

Create a file named function-with-multiple-returns.go
<pre>
package main

import "fmt"

func myFunction() (int, int) {
	return 10, 20
}

func main() {
	x, y := myFunction()  //:= is short form of declaring a new variable and initialize some value

	fmt.Println("Value of x is ", x)
	fmt.Println("Value of y is ", y)
}	
</pre>

Run it
```
go run ./function-with-multiple-returns.go
```
Expected output
![image](https://github.com/user-attachments/assets/886f2897-9b22-47ef-b048-fe64019d0c40)

## Lab - Golang pointer - pass by pointer

Create a file named pointers.go
<pre>
package main

import "fmt"

// Pass by pointer
func sayHello(msgPtr *string) {
	tmp := *msgPtr //The value stored at the address pointed by msgPtr is assigned to tmp string

	//The value stored at address pointed by msgPtr we are changing to "Hello Golang !"
	*msgPtr = tmp + " Golang " + "!"
}

func main() {

	msg := "Hello"

	//The below line will print "Hello"
	fmt.Println("Message before calling sayHello function is ", msg)

	//sayHello function is taking the address of msg string
	sayHello(&msg)

	//The below line will print "Hello Golang !"
	fmt.Println("Message after calling sayHello function is ", msg)

}
	
</pre>

Run it
```
go run ./pointers.go
```

Expected output
![image](https://github.com/user-attachments/assets/6cdee62c-ec63-4abd-a654-80171b51c458)

## Info - golang slice
<pre>
- a dynamic array
- slice can resize itself on demand at runtime to fit the new values
- internally slice uses golang fixed size array
- when we add a new value beyond the size of slice, it dynamically creates a new array copying the old values into the new array and then it adds the new last element
- this is how, slice supports dynamic size
</pre>

## Lab - Golang slice

Let's create a file called slice.go
<pre>
package main

import "fmt"

func main() {

	//shorter syntax to declare and initialize an array of int with 6 values
    //index            0   1   2 	3  4   5
	intArray := [6]int{10, 20, 30, 40, 50, 60}

	fmt.Println("Array elements are ...")
	fmt.Println(intArray)

	//Slice uses an array internally
	//in this case, the slice is referring to an array from index position 2 to 4
	var mySlice []int = intArray[2:5] // 2 is lower bound and 5 is the upper bound index, index 5 is not included

	fmt.Println("Slice elements are ...")
	fmt.Println(mySlice)

	//Let's modify the slice at certain indices
	//When the slice is modified, it allows affects the original array that is pointed by the slice
	//myslice index starts from zero just like arrays
	mySlice[0] = 100
	mySlice[1] = 200
	mySlice[2] = 300

	fmt.Println("Slice elements are ...")
	fmt.Println(mySlice)

	fmt.Println("Array elements are ...")
	fmt.Println(intArray)
}
</pre>


Run it
```
go run ./slice.go
go build ./slice.go
./slice
```

Expected output
![image](https://github.com/user-attachments/assets/89ef4601-b314-4f4e-b9b9-4d864c377316)
![image](https://github.com/user-attachments/assets/d17a0873-2049-4db7-92a2-155d11b9901d)
![image](https://github.com/user-attachments/assets/5de5008b-371d-4934-a3d1-2cd9f72fc4f3)

## Lab - Golang map
Create a file named map.go
<pre>
package main

import "fmt"

func main() {

	//Declares a map with string type key and string type value
	//key and values can be of different types as well
	toolsPath := map[string]string{
		"java_home": "/usr/lib/jdk-11",
		"mvn_home":  "/usr/share/maven",
	}

	//Given a key, map will be able to retrieve the value
	fmt.Println("Java Home Directory : ", toolsPath["java_home"])

	//add a key,value pair into an existing map
	toolsPath["go_home"] = "/usr/go"

	//iterating a map and printing its values
	for key, value := range toolsPath {
		fmt.Println(key, value)
	}

	//delete a key-value pair from an existing map
	delete(toolsPath, "go_home")
	fmt.Println(toolsPath)

}

</pre>

Run it
```
go run ./map.go
```

Expected output
![image](https://github.com/user-attachments/assets/4522a2ab-d99a-407d-860f-28be577351d1)


## Lab - Golang struct with method

Create a file named struct.go
<pre>
package main

import "fmt"

// User-defined data type
type Rectangle struct {
	length int
	width  int
}

func (rect Rectangle) Area() int {
	area := rect.length * rect.width
	return area
}

func main() {
	rectangle := Rectangle{
		length: 100,
		width:  200,
	}

	fmt.Printf("Area of rectange : %d\n", rectangle.Area())
}	
</pre>

Run it
```
go run ./struct.go
```

Expected output
![image](https://github.com/user-attachments/assets/b5cef32e-81b2-49b6-9262-6010afd9a687)


## Lab - Accepting user inputs from command line

Create a file named userinputs.go
```
package main

import "fmt"

func main() {

	var length int
	var width int

	fmt.Print("\nEnter the length of the rectangle : ")
	fmt.Scanf("%d\n", &length)

	fmt.Print("\nEnter the width of the rectangle : ")
	fmt.Scanf("%d\n", &width)

	fmt.Println("Value of length is ", length)
	fmt.Println("Value of width is ", width)
}
```

Run it
```
go run userinputs.go
```

Expected output
![image](https://github.com/user-attachments/assets/6f427437-6257-4a7c-9095-f2e3407d415e)

## Lab - Golang modules

In this exercise, we will be creating two custom go modules,  namely hello and tektutor. Hence create two folder at the same level namely hello and tektutor ash shown below
```
cd ~/golang-practices
mkdir hello tektutor
cd hello
go mod init tektutor.org/hello
cat go.mod
go mod tidy
```
Expected output
![image](https://github.com/user-attachments/assets/b1fe38c0-8b0f-4395-ac2e-a26801b4d253)

Note
<pre>
- In the above commands, the go mod init command creates a go.mod file that captures all your hello module package dependencies.	
- go mod init must be executed only when you are trying to create new module(reusable code with many .go files and reusable functions)
- go mod tidy command, will refer the go.mod file and downloads all your module dependencies (if any)
- each golang modules has one to many golang packages
</pre>


Let's create file named hello.go under the hello folder as shown below
<pre>
package hello

import "fmt"

// Whichever function starts with upper alone will be exported(made accessible outside this hello module)
func SayHello(name string) string {
	message := fmt.Sprintf("Hello, %v !", name)
	return message
}	
</pre>

Let's step out of the hello folder and get into tektutor folder
```
cd ../tektutor
go mod init tektutor.org/tektutor
cat go.mod
go mod tidy
```

Let's create a main.go under the tektutor folder
<pre>
package main

import (
   "fmt"
   "tektutor.org/hello"
)

func main() {
	msg := hello.SayHello("Golang")
	fmt.Println(msg)
}
</pre>

Now let's run the below command under tektutor folder
```
go mod tidy
go mod edit --replace tektutor.org/hello=../hello
go mod tidy
go run ./main.go
```

Expected output
![image](https://github.com/user-attachments/assets/b915ef2e-e34f-4376-a50c-3247c3ab4694)
