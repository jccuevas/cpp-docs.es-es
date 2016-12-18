---
title: "__debugbreak | Microsoft Docs"
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
  - "__debugbreak_cpp"
  - "__debugbreak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__debugbreak (intrínseco)"
  - "puntos de interrupción, __debugbreak (intrínseco)"
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __debugbreak
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Produce un punto de interrupción en el código, donde se pedirá al usuario que ejecute el depurador.  
  
## Sintaxis  
  
```  
void __debugbreak();  
```  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|------------------------|------------------|------------|  
|`__debugbreak`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## Comentarios  
 La función intrínseca del compilador `__debugbreak`, similar a [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), es una forma portable de Win32 para producir un punto de interrupción.  
  
> [!NOTE]
>  Al compilar con **\/clr**, se compilará en MSIL una función que contiene `__debugbreak`.  `asm int 3` produce una función que se va a compilar en código nativo.  Para obtener más información, vea [\_\_asm](../assembler/inline/asm.md).  
  
 Por ejemplo:  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 es similar a:  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 en un equipo x86.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)