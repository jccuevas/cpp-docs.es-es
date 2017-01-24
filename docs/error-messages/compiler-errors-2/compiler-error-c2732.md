---
title: "Error del compilador C2732 | Microsoft Docs"
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
  - "C2732"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2732"
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2732
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la especificación de vinculación se contradice con la especificación anterior para 'function'  
  
 La función ya se ha declarado con otro especificador de vinculación.  
  
 Este error puede deberse a archivos de inclusión con otros especificadores de vinculación.  
  
 Para corregir este error, cambie las instrucciones `extern` para que las vinculaciones coincidan.  En concreto, no incluya directivas `#include` en bloques `extern "C"`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2732:  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```