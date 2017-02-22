---
title: "Advertencia del compilador (nivel 1) C4237 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4237"
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la palabra clave 'palabra clave' no se puede utilizar pero está reservada para uso futuro  
  
 Una palabra clave en la especificación de C\+\+ no se implementa en el compilador de Visual C\+\+ , pero no está disponible como símbolo definido por el usuario.  
  
 El código siguiente genera el error C4237:  
  
```  
// C4237.cpp  
// compile with: /W1 /c  
int export;   // C4237  
```