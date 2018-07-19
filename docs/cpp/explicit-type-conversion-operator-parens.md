---
title: 'Operador de conversión de tipos explícita: () | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f749f8cd43588eea8476c2746134b706737b6f5
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966938"
---
# <a name="explicit-type-conversion-operator-"></a>Operador de conversión explícita de tipos: ()
C++ permite la conversión de tipos explícita mediante una sintaxis similar a la de las llamadas de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
simple-type-name ( expression-list )  
```  
  
## <a name="remarks"></a>Comentarios  
 Un *simple-type-name* seguido por un *expression-list* incluida entre paréntesis crea un objeto del tipo especificado usando las expresiones especificadas. En el ejemplo siguiente se muestra una conversión de tipo explícita al tipo int:  
  
```cpp 
int i = int( d );  
```  
  
 El ejemplo siguiente se muestra un `Point` clase.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
// expre_Explicit_Type_Conversion_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
public:  
    // Define default constructor.  
    Point() { _x = _y = 0; }  
    // Define another constructor.  
    Point( int X, int Y ) { _x = X; _y = Y; }  
  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
    void Show()   { cout << "x = " << _x << ", "  
                         << "y = " << _y << "\n"; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
int main()  
{  
    Point Point1, Point2;  
  
    // Assign Point1 the explicit conversion  
    //  of ( 10, 10 ).  
    Point1 = Point( 10, 10 );  
  
    // Use x() as an l-value by assigning an explicit  
    //  conversion of 20 to type unsigned.  
    Point1.x() = unsigned( 20 );  
    Point1.Show();  
  
    // Assign Point2 the default Point object.  
    Point2 = Point();  
    Point2.Show();  
}  
```  
  
## <a name="output"></a>Salida  
  
```Output  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 Aunque el ejemplo anterior muestra la conversión de tipos explícita mediante constantes, se puede usar la misma técnica para realizar estas conversiones en objetos. En el siguiente fragmento de código se muestra este caso:  
  
```cpp 
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 Las conversiones de tipos explícitas también se pueden especificar utilizando la sintaxis de conversión ("cast"). El ejemplo anterior, reescrito mediante la sintaxis de conversión, es:  
  
```cpp

d = (float)i;  

```  
  
 Las conversiones de estilo "cast" o de función tienen los mismos resultados cuando se convierten valores simples. Sin embargo, en la sintaxis de estilo de función, puede especificar más de un argumento para la conversión. Esta diferencia es importante para los tipos definidos por el usuario. Considere una clase `Point` y sus conversiones:  
  
```cpp

struct Point  
{  
    Point( short x, short y ) { _x = x; _y = y; }  
    ...  
    short _x, _y;  
};  
...  
Point pt = Point( 3, 10 );  

```
  
 El ejemplo anterior, que utiliza la conversión de estilo de función, muestra cómo convertir dos valores (uno para *x* y otro para *y*) para el tipo definido por el usuario `Point`.  
  
> [!CAUTION]
>  Utilice las conversiones de tipos explícitas con cuidado, ya que invalidan la comprobación de tipos integrada del compilador de C++.  
  
 El [cast](../cpp/cast-operator-parens.md) notación debe usarse para las conversiones a tipos que no tienen un *simple-type-name* (puntero o referencia de tipos, por ejemplo). Conversión a tipos que se puede expresar con una *simple-type-name* pueden escribirse en cualquiera de las formas.  
  
 La definición de tipos en las conversiones "cast" no es válida.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de postfijo](../cpp/postfix-expressions.md)   
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)