---
title: "const_mem_fun_ref_t (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::const_mem_fun_ref_t"
  - "const_mem_fun_ref_t"
  - "std.const_mem_fun_ref_t"
  - "xfunctional/std::const_mem_fun_ref_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_mem_fun_ref_t (clase)"
ms.assetid: 316ddbaa-9f46-4931-8eba-ea4ca66360ef
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# const_mem_fun_ref_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de adaptadores que permite una función miembro de **const** que no toma ningún argumento que se denomine como objeto singular de función cuando se inicializa con un argumento de referencia.  
  
## Sintaxis  
  
```  
template<class Result, class Type>  
   class const_mem_fun_ref_t  
      : public unary_function<Type, Result>   
   {  
   explicit const_mem_fun_t(Result ( Type::* _Pm)( ) const );  
   Result operator()(  
      const Type& _Left  
   ) const;  
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
 La clase de plantilla almacena una copia de `_Pm`, que debe ser un puntero a una función miembro de clase **Tipo**, en un objeto miembro privado.  Define la función `operator()` miembro como volver \(**\_Left**. \* `_Pm`\) \(\) **const**.  
  
## Ejemplo  
 El constructor de `const_mem_fun_ref_t` no se suele utilizar directamente; la función `mem_fun_ref` auxiliares se utiliza para adaptar las funciones miembro.  Vea [mem\_fun\_ref](../Topic/mem_fun_ref%20Function.md) para obtener un ejemplo de cómo utilizar adaptadores de la función miembro.  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)