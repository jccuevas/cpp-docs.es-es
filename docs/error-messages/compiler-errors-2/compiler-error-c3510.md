---
title: "Error del compilador C3510 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3510"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3510"
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3510
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede ubicar la biblioteca de tipos dependiente 'biblioteca de tipos'  
  
 [no\_registry](../../preprocessor/no-registry.md) y [auto\_search](../../preprocessor/auto-search.md) se pasaron a `#import` pero el compilador no encuentra una biblioteca de tipos a la que se hace referencia.  
  
 Para corregir este error, asegúrese de que todas las bibliotecas de tipos y las bibliotecas de tipos a las que se hace referencia están disponibles para el compilador.  
  
 El código siguiente genera el error C3510:  
  
 Se supone que se compilaron las dos bibliotecas de tipos siguientes y que se eliminó C3510a.tlb o no en la ruta de acceso.  
  
```  
// C3510a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library C3510aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]  
   enum E_C3510  
   {  
      one, two, three  
   };  
};  
```  
  
 Y, a continuación, el código fuente para la segunda biblioteca de tipos:  
  
```  
// C3510b.idl  
// post-build command: del /f C3510a.tlb  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
library C3510bLib  
{  
   importlib ("C3510a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
   struct S_C3510 {  
      enum E_C3510 e;  
   };  
};  
```  
  
 Y, a continuación, el código de cliente:  
  
```  
// C3510.cpp  
#import "c3510b.tlb" no_registry auto_search   // C3510  
int main() {  
   C3510aLib::S_C4336 ccc;  
}  
```