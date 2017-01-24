---
title: "indirect_array (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.indirect_array"
  - "valarray/std::indirect_array"
  - "std::indirect_array"
  - "indirect_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "indirect_array (clase)"
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# indirect_array (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla interna, auxiliar que admite los objetos que son subconjuntos de valarrays proporcionando operaciones entre matrices de subconjunto definido especificando un subconjunto de índices de un elemento primario valarray.  
  
## Sintaxis  
  
```  
template<class Type>  
   class indirect_array {  
public:  
   typedef Type value_type;  
   void operator=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator=(  
      const Type& x  
   ) const;  
  
   void operator*=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator/=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator%=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator+=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator-=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator^=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator&=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator|=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator<<=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator>>=(  
      const valarray<Type>& x  
   ) const;  
  
// The rest is private or implementation defined  
}  
```  
  
## Comentarios  
 La clase describe un objeto que almacena una referencia a un objeto **VA** de la clase [valarray](../standard-library/valarray-class.md)**\<Tipo\>**, junto con un objeto **xa** de la clase **valarray\<size\_t\>**, que describe la secuencia de elementos para seleccionar del objeto de **valarray\<Type\>** .  
  
 Se crea un objeto de **indirect\_array\<Type\>** sólo escribiendo una expresión de formulario **va\[xa\]**.  Las funciones miembro de clases indirect\_array se comportan como las firmas correspondientes de la función definidas para **valarray\<Type\>**, excepto que sólo la secuencia de elementos seleccionados se verá afectada.  
  
 La secuencia se compone de elementos de **xa.**[tamaño](../Topic/valarray::size.md) , donde el elemento `I` se convierte en el índice **xa**\[`I`\] dentro de **VA**.  
  
## Ejemplo:  
  
```  
// indirect_array.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // Select 2nd, 4th & 6th elements  
   // and assign a value of 10 to them  
   valarray<size_t> indx ( 3 );  
   indx [0] = 2;  
   indx [1] = 4;  
   indx [2] = 6;  
   va[indx] = 10;  
  
   cout << "The modified operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### Resultados  
  
```  
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The modified operand valarray is:  ( 0 -1 10 -1 10 -1 10 -1 8 -1 ).  
```  
  
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)