---
title: "Advertencia del compilador (nivel 1) C4230 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4230"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4230"
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4230
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado un anacronismo : los modificadores y calificadores están intercalados; se ha omitido el calificador  
  
 El uso de un calificador delante de un modificador de Microsoft como `__cdecl` supone una práctica obsoleta.  
  
## Ejemplo  
  
```  
// C4230.cpp  
// compile with: /W1 /LD  
int __cdecl const function1();   // C4230 const ignored  
```