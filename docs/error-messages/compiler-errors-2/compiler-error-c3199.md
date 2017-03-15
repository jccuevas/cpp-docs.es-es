---
title: "Error del compilador C3199 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3199"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3199"
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3199
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

uso no válido de pragmas de punto flotante: no se admiten excepciones en el modo no preciso  
  
 La pragma [float\_control](../../preprocessor/float-control.md) se utilizó para especificar el modelo de excepción en punto flotante con una configuración de [\/fp](../../build/reference/fp-specify-floating-point-behavior.md) distinta de **\/fp:precise**.  
  
 El código siguiente genera el error C3199:  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```