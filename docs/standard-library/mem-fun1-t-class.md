---
title: "mem_fun1_t (Clase) | Microsoft Docs"
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
  - "mem_fun1_t"
  - "std.mem_fun1_t"
  - "std::mem_fun1_t"
  - "xfunctional/std::mem_fun1_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun1_t (clase)"
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mem_fun1_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de adaptadores que permite llamar a una función miembro **non\_const** que toma un solo argumento como un objeto de función binaria cuando se inicializa con un argumento de puntero.  
  
## Sintaxis  
  
```  
template<class Result, class Type, class Arg>  
   class mem_fun1_t : public binary_function<Type *, Arg, Result> {  
      explicit mem_fun1_t(  
         Result (Type::* _Pm )( Arg )   
         );  
      Result operator()(  
         Type* _Pleft,   
         Arg _Right  
         ) const;  
   };  
```  
  
#### Parámetros  
 `_Pm`  
 Un puntero a una función miembro de clase **Tipo** para convertirse en un objeto de función.  
  
 `_Pleft`  
 El objeto que la función miembro de `_Pm` está invitada.  
  
 `_Right`  
 El argumento que se da a `_Pm`.  
  
## Valor devuelto  
 Una función binaria personalizable.  
  
## Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Tipo**, en un objeto miembro privado.  Define la función `operator()` miembro como volver \(**\_Pleft**\-\>\* `_Pm`\) \(**\_Right**\).  
  
## Ejemplo  
 El constructor de `mem_fun1_t` no se suele utilizar directamente; la función `mem_fun` auxiliares se utiliza para adaptar las funciones miembro.  Vea [mem\_fun](../Topic/mem_fun%20Function.md) para obtener un ejemplo de cómo utilizar adaptadores de la función miembro.  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)