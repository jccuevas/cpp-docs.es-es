---
title: "mem_fun_t (Clase) | Microsoft Docs"
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
  - "mem_fun_t"
  - "xfunctional/std::mem_fun_t"
  - "std::mem_fun_t"
  - "std.mem_fun_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mem_fun_t (clase)"
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mem_fun_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de adaptadores que permite llamar a una función miembro **non\_const** que no toma ningún argumento como un objeto de función unaria cuando se inicializa con un argumento de puntero.  
  
## Sintaxis  
  
```  
template<class Result, class Type>  
   class mem_fun_t : public unary_function<Type *, Result> {  
      explicit mem_fun_t(Result ( Type::*_Pm )( ) );  
      Result operator()( Type* _Pleft ) const;  
   };  
```  
  
#### Parámetros  
 `_Pm`  
 Un puntero a una función miembro de clase **Tipo** para convertirse en un objeto de función.  
  
 `_Pleft`  
 El objeto que la función miembro de `_Pm` está invitada.  
  
## Valor devuelto  
 Una función unario personalizable.  
  
## Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Tipo**, en un objeto miembro privado.  Define la función `operator()` miembro como volver \(`_Pleft`\-\>\* `_Pm`\) \(\).  
  
## Ejemplo  
 El constructor de `mem_fun_t` no se suele utilizar directamente; la función `mem_fun` auxiliares se utiliza para adaptar las funciones miembro.  Vea [mem\_fun](../Topic/mem_fun%20Function.md) para obtener un ejemplo de cómo utilizar adaptadores de la función miembro.  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<functional\>](../standard-library/functional.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)