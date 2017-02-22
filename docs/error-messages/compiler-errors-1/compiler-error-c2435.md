---
title: "Error del compilador C2435 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2435"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2435"
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C2435
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': la inicialización dinámica requiere CRT administrado, no puede compilar con \/clr:safe  
  
 La inicialización de variable global de dominio por aplicación requiere compilar CRT con `/clr:pure`, que no genera una imagen comprobable.  
  
 Para obtener más información, vea [appdomain](../../cpp/appdomain.md) y [proceso](../../cpp/process.md).  
  
 El código siguiente genera el error C2435:  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```