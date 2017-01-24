---
title: "Sobrecarga de operadores | Microsoft Docs"
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
  - "operator_cpp"
  - "operator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores no redefinibles"
  - "operator (palabra clave) [C++]"
  - "sobrecarga de operadores"
  - "operadores [C++], sobrecargar"
  - "operadores redefinibles"
ms.assetid: 56ad4c4f-dd0c-45e0-adaa-08fe98cb1f8e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Sobrecarga de operadores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `operator` declara una función especificando el significado de `operator-symbol` cuando se aplica a las instancias de una clase.  Esto proporciona al operador más de un significado, o lo "sobrecarga".  El compilador distingue entre los diferentes significados de un operador examinando los tipos de sus operandos.  
  
## Sintaxis  
  
```  
  
type operator operator-symbol ( parameter-list )  
```  
  
## Comentarios  
 Se puede redefinir la función de la mayoría de los operadores integrados de forma global o clase a clase.  Los operadores sobrecargados se implementan como funciones.  
  
 El nombre de un operador sobrecargado es `operator``x`, donde `x` es el operador tal como aparece en la tabla siguiente.  Por ejemplo, para sobrecargar el operador de suma, se define una función denominada `operator+`.  Del mismo modo, para sobrecarga el operador de suma y asignación, `+=`, se define una función denominada `operator+=`.  
  
### Operadores redefinibles  
  
|Operador|Nombre|Tipo|  
|--------------|------------|----------|  
|`,`|Coma|Binary|  
|`!`|NOT lógico|Unario|  
|`!=`|Desigualdad|Binary|  
|`%`|Módulo|Binary|  
|`%=`|Asignación y módulo|Binary|  
|`&`|AND bit a bit|Binary|  
|`&`|Dirección de|Unario|  
|`&&`|AND lógico|Binary|  
|`&=`|Asignación AND bit a bit|Binary|  
|`( )`|Llamada a función|—|  
|`( )`|Operador de conversión|Unario|  
|`*`|Multiplicación|Binary|  
|`*`|Desreferencia de puntero|Unario|  
|`*=`|Asignación y multiplicación|Binary|  
|`+`|Adición|Binary|  
|`+`|Unario más|Unario|  
|`++`|Incremento <sup>1</sup>|Unario|  
|`+=`|Asignación y suma|Binary|  
|`–`|Resta|Binary|  
|`–`|Negación unaria|Unario|  
|`––`|Decremento <sup>1</sup>|Unario|  
|`–=`|Asignación y resta|Binary|  
|`–>`|Selección de miembro|Binary|  
|`–>*`|Selección de puntero a miembro|Binary|  
|`/`|División|Binary|  
|`/=`|Asignación y división|Binary|  
|`<`|Menor que|Binary|  
|`<<`|Desplazamiento a la izquierda|Binary|  
|`<<=`|Asignación y desplazamiento a la izquierda|Binary|  
|`<=`|Menor o igual que|Binary|  
|`=`|Asignación|Binary|  
|`==`|Igualdad|Binary|  
|`>`|Mayor que|Binary|  
|`>=`|Mayor o igual que|Binary|  
|`>>`|Desplazamiento a la derecha|Binary|  
|`>>=`|Asignación y desplazamiento a la derecha|Binary|  
|`[ ]`|Subíndice de matriz|—|  
|`^`|OR exclusivo|Binary|  
|`^=`|Asignación y OR exclusivo|Binary|  
|`&#124;`|OR inclusivo bit a bit|Binary|  
|`&#124;=`|Asignación y OR inclusivo bit a bit|Binary|  
|`&#124;&#124;`|OR lógico|Binary|  
|`~`|Complemento a uno|Unario|  
|`delete`|`Delete`|—|  
|`new`|`New`|—|  
|`conversion operators`|operadores de conversión|Unario|  
  
 1   Existen dos versiones de los operadores de incremento y decremento unarios: preincremento y postincremento.  
  
 Vea [Reglas generales de la sobrecarga de operadores](../cpp/general-rules-for-operator-overloading.md) para obtener más información.  En los temas siguientes se describen las restricciones de las distintas categorías de operadores sobrecargados:  
  
-   [Operadores unarios](../cpp/overloading-unary-operators.md)  
  
-   [Operadores binarios](../cpp/binary-operators.md)  
  
-   [Asignación](../cpp/assignment.md)  
  
-   [Llamada a función](../cpp/function-call-cpp.md)  
  
-   [Subíndices](../cpp/subscripting.md)  
  
-   [Acceso a miembros de clase](../cpp/member-access.md)  
  
-   [Incremento y decremento](../cpp/increment-and-decrement-operator-overloading-cpp.md).  
  
-   [Conversiones](../cpp/user-defined-type-conversions-cpp.md)  
  
 Los operadores que se muestran en la tabla siguiente no se pueden sobrecargar.  La tabla incluye los símbolos de preprocesador `#` y `##`.  
  
### Operadores no redefinibles  
  
|||  
|-|-|  
|`Operator`|`Name`|  
|`.`|Selección de miembro|  
|`.*`|Selección de puntero a miembro|  
|`::`|Resolución de ámbito|  
|`?  :`|Condicional|  
|`#`|Conversión de preprocesador en una cadena|  
|`##`|Concatenación de preprocesadores|  
  
 Aunque el compilador suele llamar implícitamente a los operadores sobrecargados cuando se encuentran en el código, se pueden invocar explícitamente de la misma manera que cualquier función miembro o no miembro:  
  
```  
Point pt;  
pt.operator+( 3 );  // Call addition operator to add 3 to pt.  
```  
  
## Ejemplo  
 En el ejemplo siguiente se sobrecarga el operador `+` para sumar dos números complejos y se devuelve el resultado.  
  
```  
// operator_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Complex {  
   Complex( double r, double i ) : re(r), im(i) {}  
   Complex operator+( Complex &other );  
   void Display( ) {   cout << re << ", " << im << endl; }  
private:  
   double re, im;  
};  
  
// Operator overloaded using a member function  
Complex Complex::operator+( Complex &other ) {  
   return Complex( re + other.re, im + other.im );  
}  
  
int main() {  
   Complex a = Complex( 1.2, 3.4 );  
   Complex b = Complex( 5.6, 7.8 );  
   Complex c = Complex( 0.0, 0.0 );  
  
   c = a + b;  
   c.Display();  
}  
```  
  
## Salida  
  
```  
6.8, 11.2  
```  
  
## En esta sección  
  
1.  [Reglas generales para la sobrecarga de operadores](../cpp/general-rules-for-operator-overloading.md)  
  
2.  [Sobrecargar operadores unarios](../cpp/overloading-unary-operators.md)  
  
3.  [Operadores binarios](../cpp/binary-operators.md)  
  
4.  [Asignación](../cpp/assignment.md)  
  
5.  [Llamada de función](../cpp/function-call-cpp.md)  
  
6.  [Subíndices](../cpp/subscripting.md)  
  
7.  [Acceso a miembros](../cpp/member-access.md)  
  
## Vea también  
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)