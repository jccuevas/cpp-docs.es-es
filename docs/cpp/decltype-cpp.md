---
title: decltype (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- decltype_cpp
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1f07590275ca6e2b65d6f3d58bcea825acc71f73
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="decltype--c"></a>decltype (C++)
El especificador de tipo `decltype` produce el tipo de una expresión especificada. El `decltype` escriba especificador, junto con el [palabra clave auto](../cpp/auto-cpp.md), es útil principalmente para los desarrolladores que crean bibliotecas de plantillas. Use `auto` y `decltype` para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla. O bien utilice `auto` y `decltype` para declarar una función de plantilla que contenga una llamada a otra función y devuelva el tipo de valor devuelto de la función contenida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
decltype( expression )  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`expression`|Una expresión. Para obtener más información, consulte [expresiones](../cpp/expressions-cpp.md).|  
  
## <a name="return-value"></a>Valor devuelto  
 Tipo del parámetro `expression`.  
  
## <a name="remarks"></a>Comentarios  
 El especificador de tipo `decltype` se admite en Visual C++ 2010 o versiones posteriores, y se puede usar con código nativo o administrado. `decltype(auto)` (C++14) se admite en Visual Studio de 2015 y versiones posteriores.  
  
 El compilador usa las siguientes reglas para determinar el tipo del parámetro `expression`.  
  
-   Si el `expression` parámetro es un identificador o un [acceso a miembros de clase](../cpp/member-access-operators-dot-and.md), `decltype(expression)` es el tipo de entidad designado por `expression`. Si no existe esa entidad o si el parámetro `expression` designa un conjunto de funciones sobrecargadas, el compilador produce un mensaje de error.  
  
-   Si el `expression` parámetro es una llamada a una función o un operador sobrecargado, `decltype(expression)` es el tipo de valor devuelto de la función. Los paréntesis alrededor de un operador sobrecargado se omiten.  
  
-   Si el `expression` parámetro es un [rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` es el tipo de `expression`. Si el `expression` parámetro es un [valor l](../cpp/lvalues-and-rvalues-visual-cpp.md), `decltype(expression)` es un [referencia lvalue](../cpp/lvalue-reference-declarator-amp.md) para el tipo de `expression`.  
  
 En el ejemplo de código siguiente se muestran algunos usos del especificador de tipo `decltype`. En primer lugar, suponga que ha incluido las siguientes instrucciones en el código.  
  
```cpp  
int var;  
const int&& fx();   
struct A { double x; }  
const A* a = new A();  
```  
  
 A continuación, examine los tipos devueltos por las cuatro instrucciones `decltype` en la tabla siguiente.  
  
|Instrucción|Tipo|Notas|  
|---------------|----------|-----------|  
|`decltype(fx());`|`const int&&`|Un [referencia rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) a una `const int`.|  
|`decltype(var);`|`int`|El tipo de variable `var`.|  
|`decltype(a->x);`|`double`|El tipo del acceso a miembros.|  
|`decltype((a->x));`|`const double&`|Los paréntesis internos hacen que la instrucción se evalúe como una expresión en lugar de como un acceso a miembros. Y como `a` se declara como un puntero `const`, el tipo es una referencia a `const double`.|  
  
## <a name="decltype-and-auto"></a>Decltype y Auto  
 En C ++ 14, puede usar `decltype(auto)` sin tipo de valor devuelto final para declarar una función de plantilla cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla.  
  
 En C++11, puede usar el especificador de tipo `decltype` en un tipo de valor devuelto final junto con la palabra clave `auto` para declarar una función de plantilla, cuyo tipo de valor devuelto depende de los tipos de sus argumentos de plantilla. Considere, por ejemplo el ejemplo de código siguiente en el que el tipo de valor devuelto de la función de plantilla depende de los tipos de los argumentos de plantilla. En el ejemplo de código, el *desconocido* marcador de posición indica que no se puede especificar el tipo de valor devuelto.  
  
```cpp  
template<typename T, typename U>  
UNKNOWN func(T&& t, U&& u){ return t + u; };   
```  
  
 La introducción del especificador de tipo `decltype` permite que el desarrollador obtenga el tipo de la expresión que devuelve la función de plantilla. Use la *sintaxis de declaración de función alternativa* que se muestra más adelante, el `auto` palabra clave y el `decltype` escriba especificador para declarar un *especificado por el tiempo de ejecución* tipo de valor devuelto. El tipo de valor devuelto especificado en tiempo de compilación se determina cuando se compila la declaración, en lugar de cuando se codifica.  
  
 El prototipo siguiente muestra la sintaxis de una declaración de función alternativa. Tenga en cuenta que la `const` y `volatile` calificadores y el `throw` [una especificación de excepción](../cpp/exception-specifications-throw-cpp.md) son opcionales. El *cuerpo_función* marcador de posición representa una instrucción compuesta que especifica lo que hace la función. Como procedimiento recomendado, de codificación el *expresión* marcador de posición en el `decltype` instrucción debe coincidir con la expresión especificada por el `return` instrucción, si hay alguno, en el *cuerpo_función*.  
  
 **Auto** *function_name* **(** *parámetros*<sub>opt</sub> **)** ** Const**<sub>opt</sub> **volátiles**<sub>opt</sub> ** -> ** **decltype (** *expresión* **)** **throw**<sub>opt</sub> **{** *cuerpo_función* **};**  
  
 En el ejemplo de código siguiente, el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `myFunc` viene determinado por los tipos de los argumentos de plantilla `t` y `u`. Como procedimiento de codificación recomendado, el ejemplo de código también utiliza referencias rvalue y la `forward` plantilla de función, que son compatibles con *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
```cpp  
//C++11  
 template<typename T, typename U>  
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))   
        { return forward<T>(t) + forward<U>(u); };  
  
//C++14  
template<typename T, typename U>  
decltype(auto) myFunc(T&& t, U&& u)   
        { return forward<T>(t) + forward<U>(u); };  
  
```  
  
## <a name="decltype-and-forwarding-functions-c11"></a>Funciones de reenvío y decltype (C++11)  
 Las funciones de reenvío encapsulan llamadas a otras funciones. Considere una plantilla de función que reenvía sus argumentos, o los resultados de una expresión en la que participan estos argumentos, a otra función. Además, la función de reenvío devuelve el resultado de la llamada a otra función. En este escenario, el tipo de valor devuelto de la función de reenvío debe ser el mismo que el tipo de valor devuelto de la función encapsulada.  
  
 En este escenario, no puede escribir una expresión de tipo adecuada sin el especificador de tipo `decltype`. El especificador de tipo `decltype` permite usar funciones de reenvío genéricas porque no pierde la información necesaria sobre si una función devuelve o no un tipo de referencia. Para obtener un ejemplo de código de una función de reenvío, vea el ejemplo anterior de la función de plantilla `myFunc`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se declara el tipo de valor devuelto especificado en tiempo de compilación de la función de plantilla `Plus()`. La función `Plus` procesa sus operandos con la sobrecarga `operator+`. Por consiguiente, la interpretación de operador más (+) y el tipo de valor devuelto de la función `Plus` depende de los tipos de los argumentos de la función.  
  
```cpp  
// decltype_1.cpp  
// compile with: cl /EHsc decltype_1.cpp  
  
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
  
```Output  
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```
  
## <a name="example"></a>Ejemplo
**Visual Studio 2017 y versiones posterior:** el compilador analiza decltype argumentos cuando las plantillas se declaran en lugar de crear una instancia. Por consiguiente, si se detecta una especialización no dependiente en el argumento decltype, no se aplaza hasta el momento de la creación de instancias, sino que se procesa inmediatamente y los errores resultantes se diagnostican en ese momento.

En el ejemplo siguiente se muestra este tipo de error del compilador que se genera en el punto de declaración:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>Requisitos  
 Visual C++ 2010 o versiones posteriores.  
  
 `decltype(auto)`requiere Visual Studio 2015 o versiones posterior.  
  

