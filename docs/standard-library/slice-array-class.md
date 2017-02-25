---
title: "slice_array (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "slice_array"
  - "valarray/std::slice_array"
  - "std.slice_array"
  - "std::slice_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "slice_array (clase)"
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# slice_array (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla interna, auxiliar que admite objetos de segmento proporcionando operaciones entre matrices de subconjunto definido en el segmento de un valarray.  
  
## Sintaxis  
  
```  
template<class Type>  
   class slice_array : public slice {  
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
 La clase describe un objeto que almacena una referencia a un objeto de clase [valarray](../standard-library/valarray-class.md)**\<Tipo\>**, junto con un objeto de clase [segmento](../standard-library/slice-class.md), que describe la secuencia de elementos para seleccionar del objeto de **valarray\<Type\>** .  
  
 La clase de plantilla se crea indirectamente en ciertas operaciones valarray y no se pueden usar directamente en el programa.  Una clase de plantilla interna, auxiliar utilizada por el operador suscrito de segmento:  
  
 ::\<`operator[]` \> \(\<`slice`\) de`slice_array`**Tipo**`valarray`**Tipo**.  
  
 Se crea un objeto de **slice\_array\<Type\>** sólo escribiendo una expresión de formulario [va &#91;sl&#93;](../Topic/valarray::operator.md), para un segmento **sl** de **VA**valarray.  Las funciones miembro de clases slice\_array se comportan como las firmas correspondientes de la función definidas para **valarray\<Type\>**, excepto que sólo la secuencia de elementos seleccionados se verá afectada.  La secuencia controlada por el slice\_array es definida por los tres parámetros del constructor del segmento, el índice del primer elemento del segmento, el número de elementos, y la distancia entre los elementos.  Un usuario slice\_array de **VA** valarray declarado por **VA**\[`slice`\(2, 5, 3\)\] selecciona los elementos con índices 2, 5, 8, 11 y 14, de **VA**.  Los índices deben ser válidos para que el procedimiento sea válidos.  
  
## Ejemplo  
 Vea el ejemplo para [slice::slice](../Topic/slice::slice.md) para obtener un ejemplo de cómo declarar y utilizar un slice\_array.  
  
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)