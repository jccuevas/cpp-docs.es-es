---
title: "nothrow (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "nothrow_cpp"
  - "nothrow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], nothrow"
  - "nothrow __declspec (palabra clave)"
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# nothrow (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Atributo extendido `__declspec` que se puede usar en la declaración de funciones.  
  
## Sintaxis  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## Comentarios  
 Este atributo indica al compilador que la función declarada y las funciones a las que llama nunca iniciarán una excepción.  Con el modelo de control asincrónico de excepciones, que ahora es el predeterminado, el compilador puede eliminar los mecanismos de seguimiento de la duración de algunos objetos que no se pueden desenredar en esa función, y reducir significativamente el tamaño del código.  Dada la directiva de preprocesador siguiente, las tres declaraciones de función que se muestran a continuación son equivalentes:  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 Con `void __declspec(nothrow) __stdcall f2();`, tiene la ventaja de que puede usar una definición de API, como la que ilustra la instrucción `#define`, para especificar fácilmente `nothrow` en un conjunto de funciones.  La tercera declaración`, void __stdcall f3() throw();`, es la sintaxis definida en el estándar de C\+\+.  
  
 Para obtener más información, vea [Control sincrónico de excepciones](http://msdn.microsoft.com/es-es/81595fae-d8ab-4c14-9670-8d6639cc0369).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)