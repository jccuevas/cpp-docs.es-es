---
title: "Operador de conversión de tipos explícita: () | Documentos de Microsoft"
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
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 09afbed7f5a399b9ca192ff57be1c866baf59626
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="explicit-type-conversion-operator-"></a>Operador de conversión explícita de tipos: ()
C++ permite la conversión de tipos explícita mediante una sintaxis similar a la de las llamadas de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
simple-type-name ( expression-list )  
```  
  
## <a name="remarks"></a>Comentarios  
 A *simple-type-name* seguido por un *expression-list* incluida entre paréntesis crea un objeto del tipo especificado usando las expresiones especificadas. En el ejemplo siguiente se muestra una conversión de tipo explícita al tipo int:  
  
```  
int i = int( d );  
```  
  
 El ejemplo siguiente muestra un `Point` clase.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
## <a name="output"></a>Resultado  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 Aunque el ejemplo anterior muestra la conversión de tipos explícita mediante constantes, se puede usar la misma técnica para realizar estas conversiones en objetos. En el siguiente fragmento de código se muestra este caso:  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 Las conversiones de tipos explícitas también se pueden especificar utilizando la sintaxis de conversión ("cast"). El ejemplo anterior, reescrito mediante la sintaxis de conversión, es:  
  
```  
d = (float)i;  
```  
  
 Las conversiones de estilo "cast" o de función tienen los mismos resultados cuando se convierten valores simples. Sin embargo, en la sintaxis de estilo de función, puede especificar más de un argumento para la conversión. Esta diferencia es importante para los tipos definidos por el usuario. Considere una clase `Point` y sus conversiones:  
  
```  
struct Point  
{  
    Point( short x, short y ) { _x = x; _y = y; }  
    ...  
    short _x, _y;  
};  
...  
Point pt = Point( 3, 10 );  
```  
  
 El ejemplo anterior, que usa la conversión de estilo de función, muestra cómo convertir dos valores (uno para *x* y otro para *y*) para el tipo definido por el usuario `Point`.  
  
> [!CAUTION]
>  Utilice las conversiones de tipos explícitas con cuidado, ya que invalidan la comprobación de tipos integrada del compilador de C++.  
  
 El [conversión](../cpp/cast-operator-parens.md) notación debe usarse para las conversiones a tipos que no tienen un *simple-type-name* (puntero o referencia de tipos, por ejemplo). Conversión de tipos que se pueden expresar con un *simple-type-name* pueden escribirse en cualquiera de las formas. Vea [especificadores de tipo](http://msdn.microsoft.com/en-us/34b6c737-0ef1-4470-9b77-b26e46c0bbd4) para obtener más información sobre qué constituye una *simple-type-name*.  
  
 La definición de tipos en las conversiones "cast" no es válida.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de postfijo](../cpp/postfix-expressions.md)   
 [Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
