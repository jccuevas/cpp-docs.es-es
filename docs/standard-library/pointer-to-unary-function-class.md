---
title: "pointer_to_unary_function (Clase) | Microsoft Docs"
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
  - "xfunctional/std::pointer_to_unary_function"
  - "pointer_to_unary_function"
  - "std.pointer_to_unary_function"
  - "std::pointer_to_unary_function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pointer_to_unary_function (clase)"
  - "pointer_to_unary_function (función)"
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pointer_to_unary_function (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Convierte un puntero a función unaria en una función unaria adaptable.  
  
## Sintaxis  
  
```  
template<class Arg, class Result>  
class pointer_to_unary_function  
    : public unary_function<Arg, Result>   
    {  
    public:  
        explicit pointer_to_unary_function(  
            Result (*_pfunc)(Arg)  
        );  
        Result operator()(  
            Arg _Left  
        ) const;  
    };  
```  
  
#### Parámetros  
 `_pfunc`  
 La función binaria que se va a convertir.  
  
 `_Left`  
 El objeto que el *\*\_pfunc* está invitado.  
  
## Valor devuelto  
 La clase de plantilla almacena una copia de **\_pfunc**.  Define la función `operator()` miembro como volver \(\***\_pfunc**\) \(\_Left\).  
  
## Comentarios  
 Un puntero a función unario es un objeto de función y puede pasarse a cualquier algoritmo de la biblioteca de plantillas estándar que se espera una función unario como parámetro, pero no personalizarse.  Para utilizarlo con un adaptador, como enlazar un valor a o utilizarlo con un negador, debe proporcionarse con tipos anidados **argument\_type** y **result\_type** que crean tal adaptación posible.  La conversión por `pointer_to_unary_function` permite a los adaptadores de la función ejecutan los punteros a función binarios.  
  
## Ejemplo  
 El constructor de `pointer_to_unary_function` raramente se utiliza directamente.  Vea la función [ptr\_fun](../Topic/ptr_fun%20Function.md) auxiliar para obtener un ejemplo de cómo declarar y utilizar el predicado del adaptador de `pointer_to_unary_function` .  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)