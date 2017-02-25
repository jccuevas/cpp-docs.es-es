---
title: "Sub&#237;ndices | Microsoft Docs"
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
helpviewer_keywords: 
  - "matrices [C++], subíndices"
  - "sobrecarga de operadores, ejemplos"
  - "operadores [C++], sobrecargar"
  - "operador de subíndice"
  - "operador de subíndice, sobrecargados"
  - "subíndices"
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Sub&#237;ndices
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de subíndice \(**\[ \]**\), igual que el operador de llamada de función, se considera un operador binario.  El operador de subíndice debe ser una función miembro no estática que tome un único argumento.  Este argumento puede ser de cualquier tipo y designa el subíndice de la matriz deseado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un vector de tipo `int` que implementa la comprobación de límites:  
  
```  
// subscripting.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class IntVector {  
public:  
   IntVector( int cElements );  
   ~IntVector() { delete [] _iElements; }  
   int& operator[](int nSubscript);  
private:  
   int *_iElements;  
   int _iUpperBound;  
};  
  
// Construct an IntVector.  
IntVector::IntVector( int cElements ) {  
   _iElements = new int[cElements];  
   _iUpperBound = cElements;  
}  
  
// Subscript operator for IntVector.  
int& IntVector::operator[](int nSubscript) {  
   static int iErr = -1;  
  
   if( nSubscript >= 0 && nSubscript < _iUpperBound )  
      return _iElements[nSubscript];  
   else {  
      clog << "Array bounds violation." << endl;  
      return iErr;  
   }  
}  
  
// Test the IntVector class.  
int main() {  
   IntVector v( 10 );  
   int i;  
  
   for( i = 0; i <= 10; ++i )  
      v[i] = i;  
  
   v[3] = v[9];  
  
   for ( i = 0; i <= 10; ++i )  
      cout << "Element: [" << i << "] = " << v[i] << endl;  
}  
```  
  
  **Infracción de límites de matriz.**  
**Elemento: \[0\] \= 0**  
**Elemento: \[1\] \= 1**  
**Elemento: \[2\] \= 2**  
**Elemento: \[3\] \= 9**  
**Elemento: \[4\] \= 4**  
**Elemento: \[5\] \= 5**  
**Elemento: \[6\] \= 6**  
**Elemento: \[7\] \= 7**  
**Elemento: \[8\] \= 8**  
**Elemento: \[9\] \= 9**  
**Infracción de límites de matriz.**  
**Elemento: \[10\] \= 10**   
## Comentarios  
 Cuando `i` llega a 10 en el programa anterior, `operator[]` detecta que se está utilizando un subíndice fuera de los límites y emite un mensaje de error.  
  
 Observe que la función `operator[]` devuelve un tipo de referencia.  Esto lo convierte en un valor L, que permite utilizar expresiones con subíndice en cada lado de los operadores de asignación.  
  
## Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)