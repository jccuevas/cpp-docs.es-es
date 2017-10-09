---
title: Error del compilador C2289 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2289
dev_langs:
- C++
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6c771780ad3bbaefd51be10c9ff1454127f8439b
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2289"></a>Error del compilador C2289
el mismo calificador de tipo se ha utilizado más de una vez  
  
 Una definición o declaración de tipo utiliza un calificador de tipo (`const`, `volatile`, `signed`o `unsigned`) más de una vez, lo que provoca un error de compatibilidad con ANSI (**/Za**).  
  
 El ejemplo siguiente genera la advertencia C2286:  
  
```  
// C2289.cpp  
// compile with: /Za /c  
volatile volatile int i;   // C2289  
volatile int j;   // OK  
```
