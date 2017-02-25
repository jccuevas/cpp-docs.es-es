---
title: "Error del compilador C2588 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2588"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2588"
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C2588
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'::~identificador' : destructor global no válido  
  
 El destructor se ha definido para algo distinto de una clase, estructura o unión.  Esto no está permitido.  
  
 Este error puede producirse debido a que falta una clase, estructura o unión en el lado izquierdo del operador de resolución de ámbito \(`::`\).  
  
 El código siguiente genera el error C2588:  
  
```  
// C2588.cpp  
~F();   // C2588  
```