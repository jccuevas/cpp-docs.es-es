---
title: "Operador de llamada de funci&#243;n: () | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "( ) (operador de llamada a función)"
  - "() (operador de llamada a función)"
  - "operador de llamada a función ( )"
  - "llamadas a funciones, funciones de C++"
  - "llamadas a funciones, operador"
  - "funciones [C++], operador de llamada a función"
  - "operadores postfijos"
ms.assetid: 50c92e59-a4bf-415a-a6ab-d66c679ee80a
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador de llamada de funci&#243;n: ()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una expresión de postfijo seguida del operador de llamada de función, **\( \)**, especifica una llamada de función.  
  
## Sintaxis  
  
```  
  
postfix-expression   
( [argument-expression-list ] )  
```  
  
## Comentarios  
 Los argumentos del operador de llamada de función son cero o más expresiones separadas por comas \(los argumentos reales de la función\).  
  
 El elemento *postfix\-expression* se debe evaluar como una dirección de función \(por ejemplo, un identificador de función o el valor de un puntero de función\) y el elemento *argument\-expression\-list* es una lista de expresiones \(separadas por comas\) cuyos valores \(los argumentos\) se pasan a la función.  El elemento *argument\-expression\-list* puede estar vacío.  
  
 El elemento *postfix\-expression* debe ser de uno de estos tipos:  
  
-   Una función que devuelve el tipo `T`.  Una declaración de ejemplo es  
  
    ```  
    T func( int i )  
    ```  
  
-   Un puntero a una función que devuelve el tipo `T`.  Una declaración de ejemplo es  
  
    ```  
    T (*func)( int i )  
    ```  
  
-   Una referencia a una función que devuelve el tipo `T`.  Una declaración de ejemplo es  
  
    ```  
    T (&func)(int i)  
    ```  
  
-   Una desreferencia de función de puntero a miembro que devuelve el tipo `T`.  Estos son algunos ejemplos de llamadas de función:  
  
    ```  
    (pObject->*pmf)();  
    (Object.*pmf)();  
    ```  
  
## Ejemplo  
 En el ejemplo siguiente se llama a la función de biblioteca estándar `strcat_s` con tres argumentos:  
  
```  
// expre_Function_Call_Operator.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string>  
  
// STL name space  
using namespace std;  
  
int main()  
{  
    enum  
    {  
        sizeOfBuffer = 20  
    };  
  
    char s1[ sizeOfBuffer ] = "Welcome to ";  
    char s2[ ] = "C++";  
  
    strcat_s( s1, sizeOfBuffer, s2 );  
  
    cout << s1 << endl;  
}  
```  
  
  **Welcome to C\+\+**   
## Resultados de la llamada de función  
 Una llamada de función se evalúa como un valor R a menos que la función se declare como un tipo de referencia.  Las funciones con tipo de valor devuelto de referencia se evalúan como valores L y se pueden utilizar en el lado izquierdo de una instrucción de asignación, de la manera siguiente:  
  
```  
// expre_Function_Call_Results.cpp  
// compile with: /EHsc  
#include <iostream>  
class Point  
{  
public:  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
using namespace std;  
int main()  
{  
    Point ThePoint;  
  
    ThePoint.x() = 7;           // Use x() as an l-value.  
    unsigned y = ThePoint.y();  // Use y() as an r-value.  
  
    // Use x() and y() as r-values.  
    cout << "x = " << ThePoint.x() << "\n"  
         << "y = " << ThePoint.y() << "\n";  
}  
```  
  
 El código anterior define una clase denominada `Point`, que contiene objetos de datos privados que representan coordenadas *x* e *y*.  Estos objetos de datos se deben modificar y sus valores se deben recuperar.  Este programa es solo uno de varios diseños para esa clase; el uso de las funciones `GetX` y `SetX` o `GetY` y `SetY` es otro diseño posible.  
  
 Las funciones que devuelven tipos de clase, punteros a tipos de clase o referencias a tipos de clase se pueden utilizar como operando izquierdo para operadores de selección de miembros.  Por consiguiente, el código siguiente es legal.  
  
```  
// expre_Function_Results2.cpp  
class A {  
public:  
   A() {}  
   A(int i) {}  
   int SetA( int i ) {  
      return (I = i);  
   }  
  
   int GetA() {  
      return I;  
   }  
  
private:  
   int I;  
};  
  
A func1() {  
   A a = 0;  
   return a;  
}  
  
A* func2() {  
   A *a = new A();  
   return a;  
}  
  
A& func3() {  
   A *a = new A();  
   A &b = *a;  
   return b;  
}  
  
int main() {  
   int iResult = func1().GetA();  
   func2()->SetA( 3 );  
   func3().SetA( 7 );  
}  
```  
  
 Las funciones se pueden llamar de forma recursiva.  Para obtener más información sobre las declaraciones de función, vea [Especificadores de función](../misc/function-specifiers.md) y [Funciones miembro](../misc/member-functions-cpp.md).  El material relacionado está en [Programa y vinculación](../cpp/program-and-linkage-cpp.md).  
  
## Vea también  
 [Expresiones postfijas](../cpp/postfix-expressions.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Llamada de función](../c-language/function-call-c.md)   
 [\(NOTINBUILD\) Function Declarations](http://msdn.microsoft.com/es-es/3f9b4e14-60d2-47c1-acd8-4fa8fc988be7)