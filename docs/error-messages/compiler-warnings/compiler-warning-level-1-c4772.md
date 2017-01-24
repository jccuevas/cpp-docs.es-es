---
title: "Advertencia del compilador (nivel 1) C4772 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4772"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4772"
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4772
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import hace referencia a un tipo de una biblioteca de tipos que falta; se ha utilizado 'falta\_tipo' como marcador de posición  
  
 Se ha hecho referencia a una biblioteca de tipos mediante la directiva [\#import](../../preprocessor/hash-import-directive-cpp.md).  Sin embargo, la biblioteca de tipos contiene una referencia a otra biblioteca de tipos a la que no se ha hecho referencia mediante `#import`.  El compilador no ha encontrado este otro archivo .tlb.  
  
 Observe que el compilador no encontrará las bibliotecas de tipos en directorios diferentes si utiliza la opción del compilador [\/I \(Directorios de inclusión adicionales\)](../../build/reference/i-additional-include-directories.md) para especificar esos directorios.  Si desea que el compilador encuentre las bibliotecas de tipos en directorios diferentes, agregue esos directorios a la variable de entorno PATH.  
  
 Esta advertencia, de forma predeterminada, se emite como un error.  La advertencia C4772 no se puede evitar con \/W0.  
  
## Ejemplo  
 Ésta es la primera biblioteca de tipos necesaria para reproducir la advertencia C4772.  
  
```  
// c4772a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library C4772aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]  
   enum E_C4772a  
   {  
      one, two, three  
   };  
};  
```  
  
## Ejemplo  
 Ésta es la segunda biblioteca de tipos necesaria para reproducir la advertencia C4772.  
  
```  
// c4772b.idl  
// post-build command: del /f C4772a.tlb  
// C4772a.tlb is available when c4772b.tlb is built  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
library C4772bLib  
{  
   importlib ("c4772a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
   struct S_C4772b  
   {  
      enum E_C4772a e;  
   };  
};  
```  
  
## Ejemplo  
 El código siguiente genera el error C4772:  
  
```  
// C4772.cpp  
// assumes that C4772a.tlb is not available to the compiler  
// #import "C4772a.tlb"  
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve  
                       // and make sure c4772a.tlb is on disk  
```