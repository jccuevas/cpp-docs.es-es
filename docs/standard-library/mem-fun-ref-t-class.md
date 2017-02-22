---
title: "mem_fun_ref_t (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::mem_fun_ref_t"
  - "mem_fun_ref_t"
  - "std.mem_fun_ref_t"
  - "std::mem_fun_ref_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun_ref_t (clase)"
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# mem_fun_ref_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de adaptadores que permite llamar a una función miembro **non\_const** que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de referencia.  
  
## Sintaxis  
  
```  
template<class Result, class Type>  
   class mem_fun_ref_t : public unary_function<Type, Result> {  
      explicit mem_fun_ref_t(  
         Result ( Type::*_Pm )( )   
      );  
      Result operator()( Type& _Left ) const;  
   };  
```  
  
#### Parámetros  
 `_Pm`  
 Un puntero a una función miembro de clase **Tipo** para convertirse en un objeto de función.  
  
 `_Left`  
 El objeto que la función miembro de `_Pm` está invitada.  
  
## Valor devuelto  
 Una función unario personalizable.  
  
## Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Tipo**, en un objeto miembro privado.  Define la función `operator()` miembro como volver \(**\_Left**. \* `_Pm`\) \(\).  
  
## Ejemplo  
 El constructor de `mem_fun_ref_t` no se suele utilizar directamente; la función `mem_fun_ref` auxiliares se utiliza para adaptar las funciones miembro.  Vea [mem\_fun\_ref](../Topic/mem_fun_ref%20Function.md) para obtener un ejemplo de cómo utilizar adaptadores de la función miembro.  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)