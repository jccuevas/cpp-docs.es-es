---
title: "Error del compilador C2879 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2879"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2879"
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2879
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : sólo se puede proporcionar un nombre alternativo a un espacio de nombres existente mediante una definición de alias de espacio de nombres  
  
 No se puede crear un [alias de espacio de nombres](../../misc/namespace-alias.md) de un símbolo que no sea un espacio de nombres.  
  
 El código siguiente genera el error C2879:  
  
```  
// C2879.cpp  
int main() {  
   int i;  
   namespace A = i;   // C2879 i is not a namespace  
}  
```