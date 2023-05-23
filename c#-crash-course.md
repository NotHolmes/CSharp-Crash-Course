# C# (Super) Crash Course
A C# (Super) Crash Course in Thai

## Do not forget
- จบบรรทัดด้วย `;` เสมอ
- ให้เริ่มเขียนโปรแกรมใน Main ตลอดเวลา (เหตุผลเพราะเกี่ยวกับเรื่องของ Class เอาไว้ทีหลัง)
```C#
using System;
public class Hello --> ตรงนี้จะตรงกับชื่อไฟล์เสมอ
{
    public static void Main()
        {
            (เริ่มเขียนตรงนี้...)
        }
}
``` 

## Output ข้อความ
- ใช้คำสั่ง `System.Console.WriteLine("Hello");`
- สามารถ concat (+) string ได้ เช่น

```c#
System.Console.WriteLine("Hello" + "World");
-----------------------------

Output : HelloWorld
```
- สามารถพิมพ์ ตัวเลข(int, float, double) ตัวอักษร(string) ตัวแปร หรือ สมการได้
เช่น 

```c#
System.Console.WriteLine(1+2);
-----------------------------

Output : 3
```  
หรือ

```c#
a = "Hello";  
System.Console.WriteLine(a);
-----------------------------

Output : Hello
```
- output แบบ format ตัวแปรเข้าไปด้วย
```c#
int x = 1, y = 2;
int sum = x + y;

string sumCalculation = String.Format("{0} + {1} = {2}", x, y, sum);

Console.WriteLine(sumCalculation);
-----------------------------

Output : 1 + 2 = 3
```


## Read Input
- ใช้คำสั่ง `System.Console.ReadLine();`
- `System.Console.WriteLine(Console.ReadLine());` จะรอรับค่าจากคีย์บอร์ด แล้ว print ออกมาทันที
- หรือถ้าต้องการเก็บค่าที่รับเข้ามาต้องเอา string มารับ เช่น 
- 
```C#
string input = Console.ReadLine();

// (สมมติว่าพิมพ์ 123 แล้วกด Enter)

System.Console.WriteLine(input);
-----------------------------

Output : 123
```

## Variables and Types ตัวแปร และ ประเภทข้อมูล

```c#
int myInt = 1; // จำนวนเต็ม
float myFloat = 1f; // ทศนิยม
bool myBoolean = true; // มี 2 ค่า คือ true และ false
string myName = "John"; 
char myChar = 'a'; // ตัวอักษร 1 ตัว
double myDouble = 1.75; // เอาไว้เก็บทศนิยม . เยอะ ๆ 
```

## Type Conversion เปลี่ยนประเภทตัวแปร
- อยากให้ทศนิยมหายไป ให้เป็น int แทน : `int myVar = (int) 1.0;`
- เปลี่ยนจากเลขเป็น string : `string myVar = Convert.ToString(10);`

## Conditionals เงื่อนไข
- ใช้ `if` และ `else` เช่น

```c#
int a = 4;
int b = 5;

if (a == b)
{
    Console.WriteLine("equal");
}
else
{
    Console.WriteLine("no equal");
}
-----------------------------

Output : no equal
```
- ตัวอย่างเพิ่มเติม

```c#
int a = 4;
int b = 5;
bool result;

result = a < b; // true
result = a > b; // false
result = a <= 4; // a smaller or equal to 4 - true
result = b >= 6; // b bigger or equal to 6 - false
result = a == b; // = สองตัวคือเทียบว่า a = b หรือไม่ - false
result = a != b; // เทียบว่า a ไม่เท่ากับ b หรือไม่ - true
result = a > b || a < b; // เครื่องหมาย 'หรือ' - true
result = 3 < a && a < 6; // เครื่องหมาย 'และ' - true
result = !result; // นิเสธ
```

## Arrays
- ถ้า `int number = 1;` คือตัวแปร 1 ตัว
- แต่ถ้า `int[] numbers = {1, 2, 3};` คือตัวแปร 3 ตัว (เพิ่ม `[]` ตอนประกาศตัวแปรเพื่อบอกว่าเป็น Array)
- สามารถเข้าถึงตัวแปรแต่ละตัวใน Array ได้ด้วยการใส่ index **โดยที่ตัวแรกเริ่มด้วย 0**

```c#
int[] numbers = {1, 2, 3};
//--------------[0][1][2]

Console.WriteLine(numbers[0]);
-----------------------------

Output : 1
```

- สามารถประกาศ Array ว่างได้ `int[] numbers = new int[10];` โดยที่ 10 คือจำนวนตัวแปรที่ต้องการ ข้างในจะไม่มีข้อมูลอะไร เข้าถึงได้ด้วย index แบบด้านบน
- มี Multidimensional Array (เหมือน Matrix) คือ Array มีมากกว่า 1 มิติ เช่น `int[,] numbers = new int[2, 2];` (ประกาศด้วย int[,] หรือ float[,]) คือ Array 2 มิติ ขนาด 2x2 หรือ 4 ตัว (ในที่นี้)
```c#
int[,] numbers = new int[2, 2];

// [0,0] [0,1]
// [1,0] [1,1]
```

## Lists
- ประกาศ List ด้วย `List<int> numbers = new List<int>();` โดยที่ int คือประเภทข้อมูลที่จะใส่ใน List เป็น string, float, double, อื่น ๆ ได้
- เพิ่มหรือลบข้อมูลใน List ได้
```c#
List<int> numbers = new List<int>();

numbers.Add(10); // เพิ่ม 1 ใน List
numbers.Add(5); // เพิ่ม 2 ใน List
numbers.Add(3); // เพิ่ม 3 ใน List

numbers.Remove(5); // ลบ 1 ออกจาก List
numbers.RemoveAt(0); // ลบด้วย Index

// List จะมีค่าเป็น [3]

Console.WriteLine(numbers.Count); // จำนวนข้อมูลใน List
-----------------------------

Output : 1
```
- เอา List มาต่อกัน

```c#
List<string> food = new List<string>();
food.Add("apple");
food.Add("banana");

List<string> vegetables = new List<string>();
vegetables.Add("tomato");
vegetables.Add("carrot");

food.AddRange(vegetables);
Console.WriteLine(food.Count);
-----------------------------

Output : 4
```
## Loops
- ไม่ต่างจากใน C มาก
- `break` ใช้หยุด Loop ได้
- `continue` ใช้ข้ามไปที่ loop ถัดไปทันที

```c#
int i;

for(i = 0; i < 10; i++)
{
    
}
```
```c#
for(int i = 0; i < 16; i++)
{

    if(i % 2 == 1)
    {
        continue;
    }

    Console.WriteLine(i);

}
-----------------------------

Output : 0 2 4 6 8 10 12 14
```

### Foreach loop
- ใช้ลูปไปในแต่ละค่าของ Array หรือ List ได้ เริ่มจากตัวแรกจนตัวสุดท้าย เช่น
```c#
string[] programming = {"C++", "C#", "CPython", "C", "Java", "JavaScript"}; //An array

foreach (string language in programming)
{
   Console.WriteLine(language);
}
```
```
-----------------------------
Output : C++ C# CPython C Java JavaScript
```
- รูปแบบ

```c#
foreach (type variable in array)
{
  //Code
}
```

### While Loops
- คล้ายกับ [For Loops](#loops) แต่เป็นการลูปจนกว่าเงื่อนไขจะเป็นเท็จ

```c#
int n = 0;

while(n == 0)
{
    Console.WriteLine("N is 0");
    n++;
}
-----------------------------

Output : N is 0 // print รอบเดียวเพราะเข้าลูป n ก็กลายเป็น 1 แล้วและหลุด condition n == 0
```

Refereces : https://www.learncs.org