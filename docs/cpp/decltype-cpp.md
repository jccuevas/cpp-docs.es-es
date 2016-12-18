---
title: "decltype (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "decltype"
  - "decltype_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "decltype (operador)"
  - "operadores [C++], decltype"
  - "operadores [C++], deducir tipo de expresión"
  - "operadores [C++], tipo de una expresión"
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# decltype (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El especificador de tipo `decltype` produce el tipo de una expresión especificada.  El especificador de tipo `decltype`, junto con la [palabra clave auto](../cpp/auto-cpp.md), es útil sobre todo para los desarrolladores que crean bibliotecas de plantilla.  Use `auto` y `decltype` para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.  O bien utilice `auto` y `decltype` para declarar una función de plantilla que contenga una llamada a otra función y devuelva el tipo de valor devuelto de la función contenida.  
  
## Sintaxis  
  
```  
decltype( expression )  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`expression`|Una expresión.  Para obtener más información, consulte [Expresiones](../cpp/expressions-cpp.md).|  
  
## Valor devuelto  
 Tipo del parámetro `expression`.  
  
## Comentarios  
 El especificador de tipo `decltype` se admite en Visual C\+\+ 2010 o versiones posteriores, y se puede usar con código nativo o administrado.  `decltype(auto)` \(C\+\+14\) se admite en Visual Studio de 2015 y versiones posteriores.  
  
 El compilador usa las siguientes reglas para determinar el tipo del parámetro `expression`.  
  
-   Si el parámetro `expression` es un identificador o un [acceso a miembros de clase](../cpp/member-access-operators-dot-and.md), `decltype(``expression``)` es el tipo de entidad designado por `expression`.  Si no existe esa entidad o si el parámetro `expression` designa un conjunto de funciones sobrecargadas, el compilador produce un mensaje de error.  
  
-   Si el parámetro `expression` es una llamada a una función o una función de operador sobrecargada, `decltype(``expression``)` es el tipo de valor devuelto de la función.  Los paréntesis alrededor de un operador sobrecargado se omiten.  
  
-   Si el parámetro `expression` es un [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(``expression``)` es el tipo de `expression`.  Si el parámetro de `expression` es [l](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(``expression``)` es una [referencia lvalue](../cpp/lvalue-reference-declarator-amp.md) al tipo de `expression`.  
  
 En el ejemplo de código siguiente se muestran algunos usos del especificador de tipo `decltype`.  En primer lugar, suponga que ha incluido las siguientes instrucciones en el código.  
  
```  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 A continuación, examine los tipos devueltos por las cuatro instrucciones `decltype` en la tabla siguiente.  
  
|Instrucción|Tipo|Notas|  
|-----------------|----------|-----------|  
|`decltype(fx());`|`const int&&`|Una [referencia rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) a `const int`.|  
|`decltype(var);`|`int`|El tipo de variable `var`.|  
|`decltype(a->x);`|`double`|El tipo del acceso a miembros.|  
|`decltype((a->x));`|`const double&`|Los paréntesis internos hacen que la instrucción se evalúe como una expresión en lugar de como un acceso a miembros.  Y como `a` se declara como un puntero `const`, el tipo es una referencia a `const double`.|  
  
## Decltype y Auto  
 En C\+\+14, puede usar  `decltype(auto)` sin tipo de valor devuelto final para declarar una función de plantilla, cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.  
  
 En C\+\+11, puede usar el especificador de tipo `decltype` en un tipo de valor devuelto final junto con la palabra clave `auto` para declarar una función de plantilla, cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.  Considere, por ejemplo el ejemplo de código siguiente en el que el tipo de valor devuelto de la función de plantilla depende de los tipos de los argumentos de plantilla.  En el ejemplo de código, el marcador de posición *UNKNOWN* indica que no se puede especificar el tipo de valor devuelto.  
  
```  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 La introducción del especificador de tipo `decltype` permite que el desarrollador obtenga el tipo de la expresión que devuelve la función de plantilla.  Utilice la *sintaxis de declaración de función alternativa* que se muestra más adelante, la palabra clave `auto` y el especificador de tipo `decltype` para declarar un tipo de valor devuelto *especificado en tiempo de compilación*.  El tipo de valor devuelto especificado en tiempo de compilación se determina cuando se compila la declaración, en lugar de cuando se codifica.  
  
 El prototipo siguiente muestra la sintaxis de una declaración de función alternativa.  Tenga en cuenta que los calificadores `const` y `volatile` y la [especificación de la excepción](../cpp/exception-specifications-throw-cpp.md) `throw` son opcionales.  El marcador de posición *cuerpo\_función* representa una instrucción compuesta que especifica la acción que realiza la función.  Como procedimiento recomendado de codificación, el marcador de posición *expresión* de la instrucción `decltype` debe coincidir con la expresión que especifica la instrucción `return`, si existe, en *cuerpo\_función*.  
  
 `auto` *cuerpo\_función*`(`*parámetros*opc`)` `const`opc `volatile`opc `−>` `decltype(`*expresión*`)` `throw`opc `{`*cuerpo\_función*`};`  
  
 En el ejemplo de código siguiente, el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `myFunc` viene determinado por los tipos de los argumentos de plantilla `t` y `u`.  Como procedimiento de codificación recomendado, en el ejemplo de código también se utilizan referencias rvalue y la plantilla de función `forward`, que admiten el *reenvío directo*.  Para obtener más información, consulte [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
```  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## Funciones de reenvío y decltype \(C\+\+11\)  
 Las funciones de reenvío encapsulan llamadas a otras funciones.  Considere una plantilla de función que reenvía sus argumentos, o los resultados de una expresión en la que participan estos argumentos, a otra función.  Además, la función de reenvío devuelve el resultado de la llamada a otra función.  En este escenario, el tipo de valor devuelto de la función de reenvío debe ser el mismo que el tipo de valor devuelto de la función encapsulada.  
  
 En este escenario, no puede escribir una expresión de tipo adecuada sin el especificador de tipo `decltype`.  El especificador de tipo `decltype` permite usar funciones de reenvío genéricas porque no pierde la información necesaria sobre si una función devuelve o no un tipo de referencia.  Para obtener un ejemplo de código de una función de reenvío, vea el ejemplo anterior de la función de plantilla `myFunc`.  
  
## Ejemplo  
 En el ejemplo de código siguiente se declara el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `Plus()`.  La función `Plus` procesa sus operandos con la sobrecarga `operator+`.  Por consiguiente, la interpretación de operador más \(\+\) y el tipo de valor devuelto de la función `Plus` depende de los tipos de los argumentos de la función.  
  
```  
// decltype_1.cpp  
// compile with: /EHsc  
//  
#include "stdafx.h"  
#include <iostream>  
#include <string>  
#include <utility>  
#include <iomanip>  
  
using namespace std;  
  
template<typename T1, typename T2>  
auto Plus(T1&& t1, T2&& t2) ->   
   decltype(forward<T1>(t1) + forward<T2>(t2))  
{  
   return forward<T1>(t1) + forward<T2>(t2);  
}  
  
class X  
{  
   friend X operator+(const X& x1, const X& x2)  
   {  
      return X(x1.m_data + x2.m_data);  
   }  
  
public:  
   X(int data) : m_data(data) {}  
   int Dump() const { return m_data;}  
private:  
   int m_data;  
};  
  
int main()  
{  
   // Integer   
   int i = 4;  
   cout <<   
      "Plus(i, 9) = " <<   
      Plus(i, 9) << endl;  
  
   // Floating point  
   float dx = 4.0;  
   float dy = 9.5;  
   cout <<     
      setprecision(3) <<   
      "Plus(dx, dy) = " <<  
      Plus(dx, dy) << endl;  
  
   // String        
   string hello = "Hello, ";  
   string world = "world!";  
   cout << Plus(hello, world) << endl;  
  
   // Custom type  
   X x1(20);  
   X x2(22);  
   X x3 = Plus(x1, x2);  
   cout <<   
      "x3.Dump() = " <<   
      x3.Dump() << endl;  
}  
```  
  
 **Resultado**  
  
 Este ejemplo de código produce los siguientes resultados.  
  
 13  
  
 13.5  
  
 Hello, world\!  
  
 42  
  
## Requisitos  
 Visual C\+\+ 2010 o versiones posteriores.  
  
 decltype\(auto\) requiere Visual Studio 2015 o versiones posteriores.  
  
## Vea también  
 [Nombres de tipo simples](http://msdn.microsoft.com/es-es/333f45cb-2c72-4d81-8e59-e346b05f55e3)