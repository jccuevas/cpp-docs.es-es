---
title: "pointer_to_binary_function (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::pointer_to_binary_function"
  - "xfunctional/std::pointer_to_binary_function"
  - "pointer_to_binary_function"
  - "std.pointer_to_binary_function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointer_to_binary_function (clase)"
  - "pointer_to_binary_function (función)"
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# pointer_to_binary_function (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Convierte un puntero a función binaria en una función binaria adaptable.  
  
## Sintaxis  
  
```  
template<class Arg1, class Arg2, class Result>  
   class pointer_to_binary_function   
   : public binary_function <Arg1, Arg2, Result>   
   {  
   public:  
   explicit pointer_to_binary_function(  
      Result (*_pfunc )( Arg1, Arg2 )   
   );  
   Result operator()(  
      Arg1 _Left,   
      Arg2 _Right  
   ) const;  
   };  
```  
  
#### Parámetros  
 `_pfunc`  
 La función binaria que se va a convertir.  
  
 `_Left`  
 El objeto izquierdo que el *\*\_pfunc* está invitado.  
  
 `_Right`  
 El objeto correcto que el *\*\_pfunc* está invitado.  
  
## Valor devuelto  
 La clase de plantilla almacena una copia de **\_pfunc**.  Define la función `operator()` miembro como volver \(\***\_pfunc**\) \(\_Left, \_Right\).  
  
## Comentarios  
 Un puntero a función binario es un objeto de función y puede pasarse a cualquier algoritmo de la biblioteca de plantillas estándar que se espera una función binaria como parámetro, pero no personalizarse.  Para utilizarlo con un adaptador, como enlazar un valor a o utilizarlo con un negador, debe proporcionarse con tipos anidados **first\_argument\_type**, **second\_argument\_type**, y **result\_type** que crean tal adaptación posible.  La conversión por `pointer_to_binary_function` permite a los adaptadores de la función ejecutan los punteros a función binarios.  
  
## Ejemplo  
 El constructor de `pointer_to_binary_function` raramente se utiliza directamente.  Vea la función [ptr\_fun](../Topic/ptr_fun%20Function.md) auxiliar para obtener un ejemplo de cómo declarar y utilizar el predicado del adaptador de `pointer_to_binary_function` .  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)