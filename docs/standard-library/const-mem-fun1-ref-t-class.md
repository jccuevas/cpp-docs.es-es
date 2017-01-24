---
title: "const_mem_fun1_ref_t (Clase) | Microsoft Docs"
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
  - "std::const_mem_fun1_ref_t"
  - "std.const_mem_fun1_ref_t"
  - "xfunctional/std::const_mem_fun1_ref_t"
  - "const_mem_fun1_ref_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_mem_fun1_ref_t (clase)"
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# const_mem_fun1_ref_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de adaptadores que permite una función miembro de **const** con un solo argumento que se denomine como un objeto binario de función cuando se inicializa con un argumento de referencia.  
  
## Sintaxis  
  
```  
template<class Result, class Type, class Arg>  
   class const_mem_fun1_ref_t  
      : public binary_function<Type, Arg, Result> {  
   explicit const_mem_fun1_ref_t( Result (Type::*_Pm )( Arg ) const );  
   Result operator()(  
      const Type& _Left,  
      Arg _Right  
   ) const;  
   };  
```  
  
#### Parámetros  
 `_Pm`  
 Un puntero a una función miembro de clase **Tipo** para convertirse en un objeto de función.  
  
 `_Left`  
 El objeto de **const** que la función miembro de `_Pm` está invitada.  
  
 `_Right`  
 El argumento que se da a `_Pm`.  
  
## Valor devuelto  
 Una función binaria personalizable.  
  
## Comentarios  
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Tipo**, en un objeto miembro privado.  Define la función `operator()` miembro como volver \(`_Left`. \* *\_Pm*\) \(`_Right`\) **const**.  
  
## Ejemplo  
 El constructor de `const_mem_fun1_ref_t` no se suele utilizar directamente; la función `mem_fun_ref` auxiliares se utiliza para adaptar las funciones miembro.  Vea [mem\_fun\_ref](../Topic/mem_fun_ref%20Function.md) para obtener ejemplos de cómo usar adaptadores de la función miembro.  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)