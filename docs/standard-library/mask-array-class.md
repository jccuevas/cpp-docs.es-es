---
title: "mask_array (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.mask_array"
  - "mask_array"
  - "std::mask_array"
  - "valarray/std::mask_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mask_array (clase)"
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# mask_array (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla auxiliar e interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre matrices de subconjuntos.  
  
## Sintaxis  
  
```  
template<class Type>  
   class mask_array {  
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
 La clase describe un objeto que almacena una referencia a un objeto **va** de la clase [valarray](../standard-library/valarray-class.md)**\<Type\>**, junto con un objeto **ba** de la clase [valarray\<bool\>](../standard-library/valarray-bool-class.md), que describe la secuencia de los elementos que se pueden seleccionar desde el objeto **valarray\<Type\>**.  
  
 Construya un objeto **mask\_array \<Type\>** escribiendo únicamente una expresión de formato [va&#91;ba&#93;](../Topic/valarray::operator.md). Las funciones miembro de la clase mask\_array se comportarán como las firmas de función correspondientes definidas para **valarray\<Type\>**, excepto en que solo la secuencia de elementos seleccionados se ve afectada.  
  
 La secuencia consta como máximo de elementos **ba.size**. Un elemento *J* solo se incluye si **ba**\[*J*\] es true. Por lo tanto, hay tantos elementos en la secuencia de elementos true en **ba**. Si `I` es el índice del elemento true más bajo en **ba**, **va**\[`I`\] es el elemento cero de la secuencia seleccionada.  
  
## Ejemplo:  
  
```  
// mask_array.cpp  
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
  
   // Use masked subsets to assign a value of 10  
   // to all elements grrater than 3 in value  
   va [va > 3 ] = 10;  
   cout << "The modified operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
### Salida  
  
```  
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The modified operand valarray is:  ( 0 -1 2 -1 10 -1 10 -1 10 -1 ).  
```  
  
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)