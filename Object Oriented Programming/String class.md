concatenation (+ operator):
```cpp
string firstName = "bob";
string lastName = "robert";
string fullName = firstName + lastName; //string concatenation

//will return "bob robert"
```

string length : .length()
```cpp
cout << fullName.length();
```

Substring between x1 and x2 (substr(x1,x2)):
```cpp
cout << fullName.substr(0,5);
```

char at index:
```cpp
cout << fullName.at(1);

//will return the character at index 1
```