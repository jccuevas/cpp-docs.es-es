---
title: "mem_fun1_ref_t (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::mem_fun1_ref_t"
  - "std::mem_fun1_ref_t"
  - "mem_fun1_ref_t"
  - "std.mem_fun1_ref_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun1_ref_t (clase)"
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# mem_fun1_ref_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de adaptadores que permite llamar a una función miembro **non\_const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de referencia.  
  
## Sintaxis  
  
```  
template<class Result, class Type, class Arg>  
   class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {  
      explicit mem_fun1_ref_t(  
         Result (Type::* _Pm )( Arg )  
      );  
      Result operator()(  
         Type& _Left,   
         Arg _Right  
      ) const;  
   };  
```  
  
#### Parámetros  
 `_Pm`  
 Un puntero a una función miembro de clase **Tipo** para convertirse en un objeto de función.  
  
 `_Left`  
 El objeto que la función miembro de `_Pm` está invitada.  
  
 `_Right`  
 El argumento que se da a `_Pm`.  
  
## Valor devuelto  
 Una función binaria personalizable.  
  
## Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Tipo**, en un objeto miembro privado.  Define la función `operator()` miembro como volver \(**\_Left**. \* `_Pm`\) \(**\_Right**\).  
  
## Ejemplo  
 El constructor de `mem_fun1_ref_t` no se suele utilizar directamente; la función `mem_fun_ref` auxiliares se utiliza para adaptar las funciones miembro.  Vea [mem\_fun\_ref](../Topic/mem_fun_ref%20Function.md) para obtener un ejemplo de cómo utilizar adaptadores de la función miembro.  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)