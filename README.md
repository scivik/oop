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
## 2 - bank account || basic class and its member functions
```cpp
#include <iostream>
#include <stdio.h>
#include <string.h>
using namespace std;
class bank{
    int acc_number;
    char person_name[100], acc_type[100];
    float acc_balance;
  public:
bank (int accno, char *name, char *acctyp, float balance){
acc_number= accno;
strcpy (person_name, name);
strcpy (acc_type, acctyp);
acc_balance = balance;
}
void deposit();
void withdraw();
void display();

};
void bank :: deposit(){
int deposit_amount;
cout<<"\n Enter deposit amount : ";
cin>>deposit_amount;
acc_balance+=deposit_amount;

}
void bank :: withdraw(){
int withdraw_amount;
cout<<"\n Enter withdraw amount : ";
cin>>withdraw_amount;
acc_balance-=withdraw_amount;
}

void bank :: display(){
cout<<"-------------------------"<<endl;
cout<<"\nAccount Number : "<<acc_number<<endl;
cout<<"Name: "<<person_name<<endl;
cout<<"Account type: "<<acc_type<<endl;
cout<<"Balance : "<< acc_balance <<endl;
}


int main(){
int accno;
char name[100], acctyp[100];
float balance;
cout<<"Enter Details"<<endl;
cout<<"----------------------------"<<endl;
cout<<"Account number: ";
cin>>accno;
cout<<"\n Name: ";
cin>>name;
cout<<"\n Account type: ";
cin>>acctyp;
cout<<"\n Balance: ";
cin>>balance;

bank b(accno, name, acctyp, balance);
b.deposit();
b.withdraw();
b.display();
}
```

## 3 DM DB || friend function

```cpp

#include <iostream>
using namespace std;
class DB;
class DM
{
private:
int meters;
float centimeters;
public:
void getdata()
{
cout << "Enter distance in meters:";
cin >> meters;
cout << "Enter distance in centimeters:";
cin >> centimeters;
}
friend void add(DM, DB);
};
class DB
{
public:
int feet;
float inches;
public:
void getdata()
{
cout << "Enter distance in feet:";
cin >> feet;
cout << "Enter distance in inches:";
cin >> inches;
}
friend void add(DM, DB);
};
void add(DM dm, DB db)
{
float total_meters = dm.meters + db.feet * 0.3048;
float total_centimeters = dm.centimeters + db.inches * 2.54;
if (total_centimeters >= 100)
{
int extra_meters = total_centimeters / 100;
total_meters += extra_meters;
total_centimeters -= extra_meters * 100;
}
cout << "Sum of distances is : " << total_meters << " meters and " << total_centimeters <<
" centimeters." << endl;
}
int main()
{
DM dm;
DB db;
cout << "Enter the distance in meters and centimeters:" << endl;
dm.getdata();
cout << "Enter the distance in feet and inches:" << endl;
db.getdata();
add(dm, db);
return 0;
};
```
## 4 - Matrix Operation || 

```cpp
#include <iostream>
#include <vector>
using namespace std;
class MAT
{
private:
vector<vector<int>> matrix;
int m, n;
public:
MAT(int m, int n)
{
this->m = m;
this->n = n;
matrix.resize(m, vector<int>(n, 0));
}
void inputMatrix()
{
cout << "Enter the elements of the matrix : " << endl;
for (int i = 0; i < m; i++)
{
for (int j = 0; j < n; j++)
{
cin >> matrix[i][j];
}
}
}
void displayMatrix()
{
cout << "The matrix is:" << endl;
for (int i = 0; i < m; i++)
{
for (int j = 0; j < n; j++)
{
cout << matrix[i][j] << " ";
}
cout << endl;
}
}
MAT add(MAT &other)
{
MAT result(m, n);
for (int i = 0; i < m; i++)
{
for (int j = 0; j < n; j++)
{
result.matrix[i][j] = matrix[i][j] + other.matrix[i][j];
}
}
return result;
}
MAT subtract(MAT &other)
{
MAT result(m, n);
for (int i = 0; i < m; i++)
{
for (int j = 0; j < n; j++)
{
result.matrix[i][j] = matrix[i][j] - other.matrix[i][j];
}
}
return result;
}
MAT multiply(MAT &other)
{
if (n != other.m)
{
throw "Invalid dimensions for matrix multiplication!";
}
MAT result(m, other.n);
for (int i = 0; i < m; i++)
{
for (int j = 0; j < other.n; j++)
{
for (int k = 0; k < n; k++)
{
result.matrix[i][j] += matrix[i][k] * other.matrix[k][j];
}
}
}
return result;
}
};
int main()
{
int m, n;
cout << "Enter the number of rows and columns for the matrix:";
cin >> m >> n;
MAT mat1(m, n), mat2(m, n);
cout << "For matrix 1:" << endl;
mat1.inputMatrix();
cout << "For matrix 2:" << endl;
mat2.inputMatrix();
cout << "Matrix 1 : " << endl;
mat1.displayMatrix();
cout << "Matrix 2 : " << endl;
mat2.displayMatrix();
MAT mat3 = mat1.add(mat2);
MAT mat4 = mat1.subtract(mat2);
MAT mat5 = mat1.multiply(mat2);
cout << "Result of addition: " << endl;
mat3.displayMatrix();
cout << "Result of subtraction: " << endl;
mat4.displayMatrix();
cout << "Result of multiplication: " << endl;
mat5.displayMatrix();
return 0;
};
```
