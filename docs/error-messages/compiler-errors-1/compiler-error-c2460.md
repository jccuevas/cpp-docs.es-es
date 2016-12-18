---
title: "Error del compilador C2460 | Microsoft Docs"
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
  - "C2460"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2460"
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2460
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador1' : utiliza 'identificador', que se está definiendo  
  
 Una clase o estructura \(`identifier2`\) se ha declarado como miembro de sí misma \(`identifier1`\)  Las definiciones recursivas de clases y estructuras no están permitidas.  
  
 El código siguiente genera el error C2460:  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 En su lugar, utilice una referencia de puntero en la clase.  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```