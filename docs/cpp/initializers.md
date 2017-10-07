---
title: Inicializadores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- array-element initializers
- initializing arrays [C++], initializers
- arrays [C++], array-element initializers
- declarators, as initializers
- initializers, array element
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d58a1d8ed688f927719411bdae29fe08969961c5
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="initializers"></a>Inicializadores
Un inicializador especifica el valor inicial de una variable. Se pueden inicializar variables en estos contextos:  
  
-   En la definición de una variable:  
  
    ```cpp  
    int i = 3;  
    Point p1{ 1, 2 };  
    ```  
  
-   Como uno de los parámetros de una función:  
  
    ```cpp  
    set_point(Point{ 5, 6 });  
    ```  
  
-   Como el valor devuelto de una función:  
  
    ```cpp  
    Point get_new_point(int x, int y) { return { x, y }; }  
    Point get_new_point(int x, int y) { return Point{ x, y }; }  
  
    ```  
  
 Los inicializadores pueden adoptar estos formatos:  
  
-   Una expresión (o una lista de expresiones separadas por comas) entre paréntesis:  
  
    ```cpp  
    Point p1(1, 2);  
    ```  
  
-   Un signo igual seguido de una expresión:  
  
    ```cpp  
    string s = "hello";  
    ```  
  
-   Una lista de inicializadores entre llaves. La lista puede estar vacía o puede consistir en un conjunto de listas, como en el ejemplo siguiente:  
  
    ```cpp  
    struct Point{  
        int x;  
        int y;  
    };  
    class PointConsumer{  
    public:  
        void set_point(Point p){};  
        void set_points(initializer_list<Point> my_list){};  
    };  
    int main() {  
        PointConsumer pc{};  
        pc.set_point({});  
        pc.set_point({ 3, 4 });  
        pc.set_points({ { 3, 4 }, { 5, 6 } });  
    }  
    ```  
  
## <a name="kinds-of-initialization"></a>Clases de inicialización  
 Hay varias clases de inicialización, que pueden producirse en distintos puntos de la ejecución de un programa. Las diferentes clases de inicialización no son mutuamente excluyentes; por ejemplo, la inicialización de la lista puede desencadenar la inicialización de un valor y en otras circunstancias, puede desencadenar la inicialización de agregado.  
  
### <a name="zero-initialization"></a>Inicialización cero  
 La inicialización cero es la configuración de una variable en un valor cero convertido implícitamente al tipo:  
  
-   Las variables numéricas se inicializan en 0 (o 0,0, 0,0000000000, etc.).  
  
-   Variables de tipo char se inicializan en `'\0'`.  
  
-   Los punteros se inicializan en `nullptr`.  
  
-   Matrices, [POD](../standard-library/is-pod-class.md) clases, estructuras y uniones tienen los miembros que se inicializa en un valor de cero.  
  
 La inicialización cero se realiza en distintos momentos:  
  
-   Al iniciarse el programa, para todas las variables con nombre que tienen duración estática. Estas variables se pueden volver a inicializar posteriormente.  
  
-   Durante la inicialización del valor, para los tipos escalares y de clase POD que se inicializan mediante llaves vacías.  
  
-   Para las matrices en las que solo se inicializa un subconjunto de sus miembros.  
  
 A continuación se muestran algunos ejemplos de inicialización cero:  
  
```cpp  
struct my_struct{  
    int i;  
    char c;  
};  
  
int i0;              // zero-initialized to 0  
int main() {  
    static float f1;  // zero-initialized to 0.000000000  
    double d{};     // zero-initialized to 0.00000000000000000  
    int* ptr{};     // initialized to nullptr  
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'  
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0  
    my_struct a_struct{};   // i = 0, c = '\0'  
}  
```  
  
### <a name="default_initialization"></a>Inicialización predeterminada  
 La inicialización predeterminada de clases, structs y uniones es la inicialización con un constructor predeterminado. Se puede llamar al constructor predeterminado sin una expresión de inicialización o con la palabra clave `new`:  
  
```cpp  
MyClass mc1;  
MyClass* mc3 = new MyClass;  
```  
  
 Si la clase, la estructura o la unión no tiene un constructor predeterminado, el compilador emite un error.  
  
 Las variables escalares se inicializan de forma predeterminada cuando se definen sin una expresión de inicialización. Tienen valores indeterminados.  
  
```cpp  
int i1;  
float f;  
char c;  
```  
  
 Las matrices se inicializan de forma predeterminada cuando se definen sin una expresión de inicialización. Cuando una matriz se inicializa de forma predeterminada, sus miembros también se inicializan de forma predeterminada y tienen valores indeterminados, como en el ejemplo siguiente:  
  
```cpp  
int int_arr[3];  
```  
  
 Si los miembros de la matriz no tienen un constructor predeterminado, el compilador emite un error.  
  
#### <a name="default-initialization-of-constant-variables"></a>Inicialización predeterminada de variables constantes  
 Las variables constantes se deben declarar junto con un inicializador. Si son tipos escalares, generan un error del compilador, y si son tipos de clase que tienen un constructor predeterminado, generan una advertencia:  
  
```cpp  
class MyClass{};  
int main() {  
    //const int i2;   // compiler error C2734: const object must be initialized if not extern  
    //const char c2;  // same error  
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results  
}  
```  
  
#### <a name="default-initialization-of-static-variables"></a>Inicialización predeterminada de variables estáticas  
 Las variables estáticas que se declaran sin un inicializador se inicializan en 0 (se convierten implícitamente al tipo):  
  
```cpp  
class MyClass {     
private:  
    int m_int;  
    char m_char;  
};  
  
int main() {  
    static int int1;       // 0  
    static char char1;     // '\0'  
    static bool bool1;   // false  
    static MyClass mc1;     // {0, '\0'}  
}  
```  
  
 Para obtener más información sobre la inicialización de objetos estáticos globales, consulte [consideraciones de inicio adicionales](../cpp/additional-startup-considerations.md).  
  
### <a name="value-initialization"></a>Inicialización de un valor  
 La inicialización de un valor se produce en los siguientes casos:  
  
-   un valor con nombre se inicializa con llaves vacías  
  
-   un objeto temporal anónimo se inicializa con paréntesis o llaves vacíos  
  
-   un objeto se inicializa con la palabra clave `new` y paréntesis o llaves vacíos  
  
 La inicialización de un valor hace lo siguiente:  
  
-   para las clases que tienen al menos un constructor público, se llama al constructor predeterminado  
  
-   para las clases que no son de unión y no tienen constructores declarados, el objeto se inicializa en cero y se llama al constructor predeterminado  
  
-   para las matrices, se inicializa el valor de cada elemento  
  
-   en todos los demás casos, la variable se inicializa en cero  
  
```cpp  
class BaseClass {    
private:  
    int m_int;  
};  
  
int main() {  
    BaseClass bc{};     // class is initialized  
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0  
    int int_arr[3]{};  // value of all members is 0  
    int a{};     // value of a is 0  
    double b{};  // value of b is 0.00000000000000000  
}  
  
```  
  
### <a name="copy-initialization"></a>Inicialización de copia  
 La inicialización de copia es la inicialización de un objeto mediante otro objeto. Se produce en los casos siguientes:  
  
-   se inicializa una variable mediante un signo igual  
  
-   se pasa un argumento a una función  
  
-   se devuelve un objeto de una función  
  
-   se produce o detecta una excepción  
  
-   se inicializa un miembro de datos no estático con un signo igual  
  
-   se inicializan los miembros class, struct y union con la inicialización de copia durante la inicialización de agregado Vea [inicialización de agregado](#agginit) para obtener ejemplos.  
  
 En el código siguiente se muestran varios ejemplos de inicialización de copia:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class MyClass{  
public:  
    MyClass(int myInt) {}  
    void set_int(int myInt) { m_int = myInt; }  
    int get_int() const { return m_int; }  
private:  
    int m_int = 7; // copy initialization of m_int  
  
};  
class MyException : public exception{};  
int main() {  
    int i = 5;              // copy initialization of i  
    MyClass mc1{ i };  
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1  
    MyClass mc1.set_int(i);    // copy initialization of parameter from i  
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()  
  
    try{  
        throw MyException();      
    }  
    catch (MyException ex){ // copy initialization of ex  
        cout << ex.what();    
    }  
}  
```  
  
 La inicialización de copia no puede invocar constructores explícitos:  
  
```cpp  
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'  
regex r = "a.*b"; // the constructor is explicit; same error  
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error  
```  
  
 En algunos casos, si el constructor de copias de la clase se ha eliminado o es inaccesible, la inicialización de copia produce un error del compilador. 
  
### <a name="direct-initialization"></a>Inicialización directa  
 La inicialización directa es la inicialización con llaves o paréntesis (no vacíos). A diferencia de la inicialización de copia, puede invocar constructores explícitos. Se produce en los casos siguientes:  
  
-   una variable se inicializa con llaves o paréntesis no vacíos  
  
-   una variable se inicializa con la palabra clave `new` y llaves o paréntesis no vacíos  
  
-   una variable se inicializa con `static_cast`  
  
-   en un constructor, las clases base y los miembros no estáticos se inicializan con una lista de inicializadores  
  
-   en la copia de una variable capturada en una expresión lambda  
  
 En el código siguiente se muestran algunos ejemplos de inicialización directa:  
  
```cpp  
class BaseClass{  
public:  
    BaseClass(int n) :m_int(n){} // m_int is direct initialized  
private:  
    int m_int;  
};  
  
class DerivedClass : public BaseClass{  
public:  
    // BaseClass and m_char are direct initialized  
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}  
private:  
    char m_char;  
};  
int main(){  
    BaseClass bc1(5);  
    DerivedClass dc1{ 1, 'c' };  
    BaseClass* bc2 = new BaseClass(7);  
    BaseClass bc3 = static_cast<BaseClass>(dc1);  
  
    int a = 1;  
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized  
    int n = func();  
}  
```  
  
### <a name="list-initialization"></a>Inicialización de lista  
 La inicialización de lista se produce cuando se inicializa una variable con una lista de inicializadores entre llaves. Se pueden usar listas de inicializadores entre llaves en los siguientes casos:  
  
-   se inicializa una variable  
  
-   se inicializa una clase con la palabra clave `new`  
  
-   se devuelve un objeto de una función  
  
-   se pasa un argumento a una función  
  
-   uno de los argumentos de una inicialización directa  
  
-   en un inicializador de miembros de datos no estáticos  
  
-   en una lista de inicializadores del constructor  
  
 En el código siguiente se muestran algunos ejemplos de inicialización de lista:  
  
```cpp  
class MyClass {  
public:  
    MyClass(int myInt, char myChar) {}    
private:  
    int m_int[]{ 3 };  
    char m_char;  
};  
class MyClassConsumer{  
public:  
    void set_class(MyClass c) {}  
    MyClass get_class() { return MyClass{ 0, '\0' }; }  
};  
struct MyStruct{  
    int my_int;  
    char my_char;  
    MyClass my_class;  
};  
int main() {  
    MyClass mc1{ 1, 'a' };  
    MyClass* mc2 = new MyClass{ 2, 'b' };  
    MyClass mc3 = { 3, 'c' };  
  
    MyClassConsumer mcc;  
    mcc.set_class(MyClass{ 3, 'c' });  
    mcc.set_class({ 4, 'd' });  
  
    MyStruct ms1{ 1, 'a', { 2, 'b' } };  
}  
```  
  
### <a name="agginit"></a>Inicialización de agregado  
 La inicialización de agregado es una forma de inicialización de lista para matrices o tipos de clase (a menudo structs o uniones) que tienen:  
  
-   ningún miembro privado o protegido  
  
-   ningún constructor proporcionado por el usuario, salvo para los constructores eliminados o establecidos como valor predeterminado explícitamente  
  
-   ninguna clase base  
  
-   ninguna función miembro virtual  
  
> [!NOTE]
>  <!--conformance note-->In Visual Studio 2015 and earlier, an aggregate is not allowed to have  brace-or-equal initializers for non-static members. This restriction was removed in the C++14 standard and implemented in Visual Studio 2017. 
  
 Los inicializadores de agregado constan de una lista de inicialización entre llaves, con o sin un signo de igualdad, como en el ejemplo siguiente:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
struct MyAggregate{  
    int myInt;  
    char myChar;  
};  
  
int main() {  
    MyAggregate agg1{ 1, 'c' };  
  
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;  
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;  
  
    int myArr1[]{ 1, 2, 3, 4 };  
    int myArr2[3] = { 5, 6, 7 };  
    int myArr3[5] = { 8, 9, 10 };  
  
    cout << "myArr1: ";  
    for (int i : myArr1){  
        cout << i << " ";  
    }  
    cout << endl;  
  
    cout << "myArr3: ";  
    for (auto const &i : myArr3) {  
        cout << i << " ";  
    }  
    cout << endl;  
}  
```  
  
 Debería ver los siguientes resultados:  
  
```  
agg1: c: 1  
agg2: d: 2  
myArr1: 1 2 3 4  
myArr3: 8 9 10 0 0  
```  
  
> [!IMPORTANT]
>  Miembros de la matriz que se han declarado pero no se inicializaron explícitamente durante la inicialización de agregado son inicializa a cero, como en `myArr3` anteriormente.  
  
#### <a name="initializing-unions-and-structs"></a>Inicializar uniones y structs  
 Si una unión no tiene un constructor, puede inicializarla con un valor único (o con otra instancia de una unión). El valor se utiliza para inicializar el primer campo no estático. Esto es diferente de la inicialización de struct, donde el primer valor del inicializador se utiliza para inicializar el primer campo, el segundo valor para inicializar el segundo campo, y así sucesivamente. Compare la inicialización de uniones y structs en el ejemplo siguiente:  
  
```cpp  
struct MyStruct {  
    int myInt;  
    char myChar;  
};  
union MyUnion {  
    int my_int;  
    char my_char;  
    bool my_bool;  
    MyStruct my_struct;  
};  
  
int main() {    
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}  
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}  
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}  
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}  
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers  
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'  
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'  
  
    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'  
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'  
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'  
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'  
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'  
}  
```  
  
#### <a name="initializing-aggregates-that-contain-aggregates"></a>Inicializar agregados que contienen agregados  
 Los tipos agregados pueden contener otros tipos agregados, como matrices de matrices, matrices de structs, etc. Estos tipos se inicializan con conjuntos anidados de llaves, por ejemplo:  
  
```cpp  
struct MyStruct {  
    int myInt;  
    char myChar;  
};  
int main() {  
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};  
    int intArr3[2][2] = {1, 2, 3, 4};    
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };  
}  
```  
  
### <a name="reference-initialization"></a>Inicialización de referencia  
 Las variables de tipo de referencia se deben inicializar con un objeto del tipo del que se deriva el tipo de referencia o con un objeto de un tipo que se pueda convertir al tipo que se deriva del tipo de referencia. Por ejemplo:  
  
```  
// initializing_references.cppint   
int iVar;  
long lVar;  
int main()   
{   long& LongRef1 = lVar;   // No conversion required.  
   long& LongRef2 = iVar;   // C2440  
   const long& LongRef3 = iVar;   // OK  
   LongRef1 = 23L;   // Change lVar through a reference.  
   LongRef2 = 11L;   // Change iVar through a reference.  
   LongRef3 = 11L;   // C3892}  
```  
  
 La única manera de inicializar una referencia con un objeto temporal consiste en inicializar un objeto temporal constante. Una vez inicializado, una variable de tipo de referencia siempre señala al mismo objeto; no se puede modificar para que señale a otro objeto.  
  
 Aunque la sintaxis puede ser igual, la inicialización de variables de tipo de referencia y la asignación a variables de tipo de referencia son semánticamente diferentes. En el ejemplo anterior, las asignaciones que modifican `iVar` y `lVar` son similares a las inicializaciones, pero tienen efectos diferentes. La inicialización especifica el objeto al que señala la variable de tipo de referencia; la asignación asigna al objeto al que se hace referencia a través de la referencia.  
  
 Dado que tanto pasar un argumento de tipo de referencia a una función como devolver un valor de tipo de referencia desde una función son inicializaciones, los argumentos formales a una función se inicializan correctamente, así como las referencias devueltas.  
  
 Las variables de tipo de referencia solo se pueden declarar sin inicializadores en lo siguiente:  
  
-   Declaraciones de función (prototipos). Por ejemplo:  
  
    ```  
    int func( int& );  
    ```  
  
-   Declaraciones de tipo de valor devuelto de función. Por ejemplo:  
  
    ```  
    int& func( int& );  
    ```  
  
-   Declaración de un miembro de clase de tipo de referencia. Por ejemplo:  
  
    ```  
    class c {public:   int& i;};  
    ```  
  
-   Declaración de una variable especificada explícitamente como `extern`. Por ejemplo:  
  
    ```  
    extern int& iVal;  
    ```  
  
 Al inicializar una variable de tipo de referencia, el compilador usa el gráfico de decisión que se muestra en la figura siguiente para elegir entre crear una referencia a un objeto o crear un objeto temporal al que señala la referencia.  
  
 ![Gráfico de decisión de inicialización de tipos de referencia](../cpp/media/vc38s71.gif "vc38S71")  
Gráfico de decisión de inicialización de tipos de referencia  
  
 Las referencias a `volatile` tipos (declarados como `volatile` *typename* ** & ** *identificador*) se pueden inicializar con `volatile` objetos del mismo tipo o con objetos que no se ha declarado como `volatile`. No pueden, sin embargo, inicializarse con **const** objetos de ese tipo. De forma similar, las referencias a **const** tipos (declarados como **const** *typename* ** & ** *identificador *) se pueden inicializar con **const** objetos del mismo tipo (o cualquier elemento que tenga una conversión a ese tipo o con objetos que no se ha declarado como **const**). No pueden, sin embargo, inicializarse con objetos `volatile` de ese tipo.  
  
 Las referencias que no se califican con la **const** o `volatile` palabra clave se puede inicializar con objetos declarados como **const** ni `volatile`.  
  
### <a name="initialization-of-external-variables"></a>Inicialización de variables externas  
 Las declaraciones de variables automáticas, estáticas y externas pueden contener a inicializadores. Sin embargo, las declaraciones de variables externas solo pueden contener inicializadores si las variables no se declaran como `extern`.
  

