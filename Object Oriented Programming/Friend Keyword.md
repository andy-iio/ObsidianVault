A non-member function can access the private and protected members of a class if it is declared as a friend of that class.

```cpp
class Mark{
private:
	int w;
	int p;
public:
	Mark(){
		p=0;
		w=0;
	}

	Mark(int p, int w){
		this->p = p;
		this->w = w;
	}
//print is not a member of the class Mark, but the friend keyword allows the print function to access the private variable of the m object.
	friend void print(Mark m);
}

void print(Mark m){
// p and w are private members but we can access them due to the friend keyword
	cout << "(" << m.p << "," << m.w << ")" << end1;
}

int main(){
	Mark m1(10,2);
	print(m1);
}
```
