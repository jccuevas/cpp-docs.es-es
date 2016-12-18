---
title: "Advertencia del compilador (nivel 1) C4399 | Microsoft Docs"
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
  - "C4399"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4399"
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4399
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : el símbolo por proceso no se debe marcar con \_\_declspec \(dllimport\) cuando se compila con \/clr:pure  
  
 Los datos de una imagen nativa o de una imagen con construcciones nativas y CLR no se pueden importar en una pura imagen.  Para solucionarlo, compile con **\/clr** \(no **\/clr:pure**\) o elimine `__declspec(dllimport)`.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4399.  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```