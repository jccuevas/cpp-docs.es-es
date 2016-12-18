---
title: "Error irrecuperable C1197 | Microsoft Docs"
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
  - "C1197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1197"
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede hacer referencia a 'mscorlib.dll\_1' porque el programa ya hacía referencia a 'mscorlib.dll\_2'  
  
 El compilador se corresponde con una versión de Common Language Runtime.  No obstante, se ha intentado hacer referencia a un archivo de Common Language Runtime de una versión anterior.  
  
 Para resolver este error, haga referencia únicamente a archivos de la versión de Common Language Runtime incluida en la versión de Visual C\+\+ con la que esté compilando.  
  
## Ejemplo  
 El código siguiente genera el error C1197:  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```