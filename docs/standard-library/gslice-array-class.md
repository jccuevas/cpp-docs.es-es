---
title: "gslice_array (Clase) | Microsoft Docs"
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
  - "std::gslice_array"
  - "gslice_array"
  - "valarray/std::gslice_array"
  - "std.gslice_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gslice_array (clase)"
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gslice_array (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla interna, auxiliar que admite objetos generales del segmento proporcionando operaciones entre matrices de subconjunto definido en el segmento general de un valarray.  
  
## Sintaxis  
  
```  
template<class Type>  
   class gslice_array : public gsplice {  
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
 La clase describe un objeto que almacena una referencia a un objeto **VA** de la clase [valarray](../standard-library/valarray-class.md)**\<Tipo\>**, junto con un objeto **gs** de la clase [gslice](../standard-library/gslice-class.md) que describe la secuencia de elementos para seleccionar del objeto de **valarray\<Type\>** .  
  
 Se crea un objeto de **gslice\_array\<Type\>** sólo escribiendo una expresión de formulario [va &#91;gs&#93;](../Topic/valarray::operator.md).  Las funciones miembro de clases gslice\_array se comportan como las firmas correspondientes de la función definidas para **valarray\<Type\>**, excepto que sólo la secuencia de elementos seleccionados se verá afectada.  
  
 La clase de plantilla se crea indirectamente en ciertas operaciones valarray y no se pueden usar directamente en el programa.  Una clase de plantilla auxiliar interno en su lugar utiliza el operador de subíndice de segmento:  
  
 ::\<`operator[]` \> \(\<**const**\>**gslice&**\) de`gslice_array`**Tipo** `valarray`**Tipo**.  
  
 Se crea un objeto de **gslice\_array\<Type\>** sólo escribiendo una expresión de formulario **va\[gsl\]**, para un segmento **gsl** de **VA**valarray.  Las funciones miembro de clases gslice\_array se comportan como las firmas correspondientes de la función definidas para **valarray\<Type\>**, excepto que sólo la secuencia de elementos seleccionados se verá afectada.  La secuencia controlada por el gslice\_array es definida por los tres parámetros del constructor del segmento, el índice del primer elemento del primer segmento, el número de elementos de cada segmento, y la distancia entre los elementos de cada segmento.  
  
 En el ejemplo siguiente:  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);  
// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 Los índices deben ser válidos para que el procedimiento sea válidos.  
  
## Ejemplo  
 Vea el ejemplo para [gslice::gslice](../Topic/gslice::gslice.md) para obtener un ejemplo de cómo declarar y utilizar un slice\_array.  
  
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)