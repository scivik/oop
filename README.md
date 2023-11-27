# oop
## 1 - Area of triangle and Circle || Function Overloading
```cpp
#include <iostream>
using namespace std;
class Area{
public:
float area(float base, float height){
return 0.5 * base * height;
}
float area(float radius){
return 3.14 * radius * radius;
}
};
int main(){
Area a;
float base, height, radius;
cout<<"Enter the base and height of the triangle: ";
cin>>base>>height;
cout<<"Area of triangle : "<<a.area(base, height)<<endl;

cout<<"Enter the radius of the circle: ";
cin>>radius;
cout<<"Area of circle : "<<a.area(radius)<<endl;
return 0;
}
```
