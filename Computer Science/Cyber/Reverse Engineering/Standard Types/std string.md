Can paste as local type in IDA
## Linux (libstdc++)
```c
struct string {  
	char* data;  
	size_t size;  
	size_t capacity;  
};
```
## Windows (MSVC) (unsure)
```c
struct string {  
	char* data;  
	char buf[8];
	size_t size;  
	size_t capacity;  
};
```