---
title: "Advertencia del compilador (nivel 4) C4336 | Microsoft Docs"
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
  - "C4336"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4336"
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4336
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

importar biblioteca de tipos 'biblio1\_tipos' con referencia cruzada antes de importar 'biblio2\_tipos'  
  
 Se ha hecho referencia a una biblioteca de tipos mediante la directiva [\#import](../../preprocessor/hash-import-directive-cpp.md).  Sin embargo, la biblioteca de tipos contiene una referencia a otra biblioteca de tipos a la que no se ha hecho referencia mediante `#import`.  El compilador ha encontrado este otro archivo .tlb.  
  
 Dadas dos bibliotecas de tipos en disco creadas a partir de los dos archivos siguientes \(compilados con midl.exe\):  
  
```  
// c4336a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library c4336aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]  
   enum E_C4336  
   {  
      one, two, three  
   };  
};  
```  
  
 La segunda biblioteca de tipos:  
  
```  
// c4336b.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
library C4336bLib  
{  
   importlib ("c4336a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
   struct S_C4336  
   {  
      enum E_C4336 e;  
   };  
};  
```  
  
 El código siguiente genera el error C4336:  
  
```  
// C4336.cpp  
// compile with: /W4 /LD  
// #import "C4336a.tlb"  
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve  
```