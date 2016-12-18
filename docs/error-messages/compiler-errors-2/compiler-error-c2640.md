---
title: "Error del compilador C2640 | Microsoft Docs"
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
  - "C2640"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2640"
ms.assetid: e4d137ab-ed1d-457c-9eec-b70d97f1b0b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2640
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : el modificador \_\_based no es válido para referencias  
  
 El modificador `__based` sólo se puede utilizar en punteros.  
  
 El código siguiente genera el error C2640:  
  
```  
// C2640.cpp  
void f(int i) {  
    void *vp;  
    int _based(vp) &vr = I;  // C2640  
}  
```