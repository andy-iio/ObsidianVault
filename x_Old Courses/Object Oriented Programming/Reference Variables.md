A reference variable is an alternate name to an existing variable (similar to a [[Pointers|pointer]] but you don't need to use * to access the value referred to by the reference.)

- cannot change the reference to refer to a different object after the initialization

```cpp
//dont need to use prefix * to access the value of reference

int original;
int& referenceToOriginal = original;

//setting the reference will also set the original
referenceToOriginal = 10;
cout << "original variable: " << original << "\n";
cout << "reference variable: " << referenceToOriginal<< "\n";

//changing the original also changes the reference
original = 20;

cout << "original variable: " << original << "\n";
cout << "reference variable: " << referenceToOriginal << "\n";
```
