---
title: "Friends de plantilla | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 077acea5-0d0f-4b33-916d-1211797e5e28
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
caps.handback.revision: 9
---
# Friends de plantilla
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las plantillas de clase pueden tener elementos [friend](http://msdn.microsoft.com/es-es/bf412640-d857-4acb-b2b5-513131cb9681).  Una clase o plantilla de clase y una función o plantilla de función pueden ser elementos friend de una clase de plantilla.  Los elementos friend también pueden ser especializaciones de una plantilla de clase o de función, pero no especializaciones parciales.  
  
## Ejemplo  
 En el ejemplo siguiente, una función friend se define como una plantilla de función dentro de la plantilla de clase.  Este código genera una versión de la función friend para cada instancia de la plantilla.  Esta construcción es útil si la función friend depende de los mismos parámetros de plantilla que la clase.  
  
```  
// template_friend1.cpp  
// compile with: /EHsc  
  
#include <iostream>  
using namespace std;  
  
template <class T> class Array {  
   T* array;  
   int size;  
  
public:  
   Array(int sz): size(sz) {  
      array = new T[size];  
      memset(array, 0, size * sizeof(T));  
   }  
  
   Array(const Array& a) {  
      size = a.size;  
      array = new T[size];  
      memcpy_s(array, a.array, sizeof(T));  
   }  
  
   T& operator[](int i) {  
      return *(array + i);  
   }  
  
   int Length() { return size; }  
  
   void print() {  
      for (int i = 0; i < size; i++)        
         cout << *(array + i) << " ";  
  
      cout << endl;  
   }  
  
   template<class T>  
   friend Array<T>* combine(Array<T>& a1, Array<T>& a2);  
};  
  
template<class T>  
Array<T>* combine(Array<T>& a1, Array<T>& a2) {  
   Array<T>* a = new Array<T>(a1.size + a2.size);  
   for (int i = 0; i < a1.size; i++)  
      (*a)[i] = *(a1.array + i);  
  
   for (int i = 0; i < a2.size; i++)  
      (*a)[i + a1.size] = *(a2.array + i);  
  
   return a;  
}  
  
int main() {  
   Array<char> alpha1(26);  
   for (int i = 0 ; i < alpha1.Length() ; i++)  
      alpha1[i] = 'A' + i;  
  
   alpha1.print();  
  
   Array<char> alpha2(26);  
   for (int i = 0 ; i < alpha2.Length() ; i++)  
      alpha2[i] = 'a' + i;  
  
   alpha2.print();  
   Array<char>*alpha3 = combine(alpha1, alpha2);  
   alpha3->print();  
   delete alpha3;  
}  
```  
  
  **A B C D E F G H I J K L M N O P Q R S T U V W X Y Z**   
**a b c d e f g h i j k l m n o p q r s t u v w x y z**   
**A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z**    
## Ejemplo  
 En el ejemplo siguiente se incluye una función friend que tiene una especialización de plantilla.  Una especialización de plantilla de función es automáticamente friend si la plantilla de función original es friend.  
  
 También se puede declarar solo la versión especializada de la plantilla como friend, como indica el comentario que precede a la declaración friend del código siguiente.  En este caso, se debe colocar la definición de especialización de plantilla friend fuera de la clase de plantilla.  
  
```  
// template_friend2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class Array;  
  
template <class T>  
void f(Array<T>& a);  
  
template <class T> class Array  
{  
    T* array;  
    int size;  
  
public:  
    Array(int sz): size(sz)  
    {  
        array = new T[size];  
        memset(array, 0, size * sizeof(T));  
    }  
    Array(const Array& a)  
    {  
        size = a.size;  
        array = new T[size];  
        memcpy_s(array, a.array, sizeof(T));  
    }  
    T& operator[](int i)  
    {  
        return *(array + i);  
    }  
    int Length()  
    {   
        return size;  
    }  
    void print()  
    {  
        for (int i = 0; i < size; i++)  
        {  
            cout << *(array + i) << " ";  
        }  
        cout << endl;  
    }  
    // If you replace the friend declaration with the int-specific  
    // version, only the int specialization will be a friend.  
    // The code in the generic f will fail  
    // with C2248: 'Array<T>::size' :  
    // cannot access private member declared in class 'Array<T>'.  
    //friend void f<int>(Array<int>& a);  
  
    friend void f<>(Array<T>& a);  
};  
  
// f function template, friend of Array<T>  
template <class T>  
void f(Array<T>& a)  
{  
    cout << a.size << " generic" << endl;  
}  
  
// Specialization of f for int arrays  
// will be a friend because the template f is a friend.  
template<> void f(Array<int>& a)  
{  
    cout << a.size << " int" << endl;  
}  
  
int main()  
{  
    Array<char> ac(10);  
    f(ac);  
  
    Array<int> a(10);  
    f(a);  
}  
```  
  
  **10 generic**  
**10 int**   
## Ejemplo  
 En el ejemplo siguiente se muestra una plantilla de clase friend declarada dentro de una plantilla de clase.  La plantilla de clase se usa como argumento de plantilla para la clase friend.  Las plantillas de clase friend se deben definir fuera de la plantilla de clase en la que se declaran.  Las especializaciones o especializaciones parciales de las plantillas friend son también elementos friend de la plantilla de clase original.  
  
```  
// template_friend3.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
class X  
{  
private:  
   T* data;  
   void InitData(int seed) { data = new T(seed); }  
public:  
   void print() { cout << *data << endl; }  
   template <class U> friend class Factory;  
};  
  
template <class U>  
class Factory  
{  
public:  
   U* GetNewObject(int seed)  
   {  
      U* pu = new U;  
      pu->InitData(seed);  
      return pu;  
   }  
};  
  
int main()  
{  
   Factory< X<int> > XintFactory;  
   X<int>* x1 = XintFactory.GetNewObject(65);  
   X<int>* x2 = XintFactory.GetNewObject(97);  
  
   Factory< X<char> > XcharFactory;  
   X<char>* x3 = XcharFactory.GetNewObject(65);  
   X<char>* x4 = XcharFactory.GetNewObject(97);  
   x1->print();  
   x2->print();  
   x3->print();  
   x4->print();  
}  
```  
  
  **65**  
**97**  
**A**  
**a**   
## Vea también  
 [Argumentos predeterminados](../cpp/default-arguments.md)