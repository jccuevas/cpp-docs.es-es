---
title: "Advertencia del compilador (nivel 1) C4518 | Microsoft Docs"
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
  - "C4518"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4518"
ms.assetid: 4ad21004-f076-43fd-99f4-4bf1f9be4c0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4518
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'especificador' : clase de almacenamiento o especificadores de tipo no esperados aquí; se han omitido  
  
 El código siguiente genera el error C4518:  
  
```  
// C4518.cpp  
// compile with: /c /W1  
_declspec(dllexport) extern "C" void MyFunction();   // C4518  
  
extern "C" void MyFunction();   // OK  
```