---
title: "Operador de conversi&#243;n expl&#237;cita de tipos: () | Microsoft Docs"
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
  - "conversiones [C++], explícita"
  - "conversión de tipos de datos [C++], explícita"
  - "operador de conversión explícita de tipos de datos"
  - "operadores [C++], conversión de tipos explícita"
  - "conversión de tipos [C++], conversiones explícitas"
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador de conversi&#243;n expl&#237;cita de tipos: ()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ permite la conversión de tipos explícita mediante una sintaxis similar a la de las llamadas de función.  
  
## Sintaxis  
  
```  
  
simple-type-name ( expression-list )  
```  
  
## Comentarios  
 Un elemento *simple\-type\-name* seguido de una *expression\-list* incluida entre paréntesis crea un objeto del tipo indicado mediante las expresiones especificadas.  En el ejemplo siguiente se muestra una conversión de tipo explícita al tipo int:  
  
```  
int i = int( d );  
```  
  
 En el ejemplo siguiente se usa una versión modificada de la clase `Point` definida en [Resultados de la llamada de función](../misc/function-call-results.md).  
  
## Ejemplo  
  
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
  
## Salida  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 Aunque el ejemplo anterior muestra la conversión de tipos explícita mediante constantes, se puede usar la misma técnica para realizar estas conversiones en objetos.  En el siguiente fragmento de código se muestra este caso:  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 Las conversiones de tipos explícitas también se pueden especificar utilizando la sintaxis de conversión \("cast"\).  El ejemplo anterior, reescrito mediante la sintaxis de conversión, es:  
  
```  
d = (float)i;  
```  
  
 Las conversiones de estilo "cast" o de función tienen los mismos resultados cuando se convierten valores simples.  Sin embargo, en la sintaxis de estilo de función, puede especificar más de un argumento para la conversión.  Esta diferencia es importante para los tipos definidos por el usuario.  Considere una clase `Point` y sus conversiones:  
  
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
  
 El ejemplo anterior, que utiliza la conversión de estilo de función, muestra cómo convertir dos valores \(uno para *x* y uno para *y*\) al tipo `Point` definido por el usuario.  
  
> [!CAUTION]
>  Utilice las conversiones de tipos explícitas con cuidado, ya que invalidan la comprobación de tipos integrada del compilador de C\+\+.  
  
 La notación de [conversión \("cast"\)](../cpp/cast-operator-parens.md) se debe utilizar para las conversiones a tipos que no tienen un elemento *simple\-type\-name* \(por ejemplo, tipos de puntero o referencia\).  La conversión a tipos que puedan expresarse con un elemento *simple\-type\-name* se puede escribir en cualquiera de las formas.  Vea [Especificadores de tipo](http://msdn.microsoft.com/es-es/34b6c737-0ef1-4470-9b77-b26e46c0bbd4) para obtener más información sobre lo que constituye un *simple\-type\-name*.  
  
 La definición de tipos en las conversiones "cast" no es válida.  
  
## Vea también  
 [Expresiones postfijas](../cpp/postfix-expressions.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)