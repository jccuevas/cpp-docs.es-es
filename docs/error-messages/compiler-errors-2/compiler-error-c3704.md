---
title: "Error del compilador C3704 | Microsoft Docs"
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
  - "C3704"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3704"
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3704
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : un método vararg no puede desencadenar eventos  
  
 Se intentó utilizar [\_\_event](../../cpp/event.md) en un método vararg.  Para corregir este error, reemplace la llamada a `fireEvent(int i, ...)` con la llamada a `fireEvent(int i)`, como se muestra en el ejemplo de código siguiente.  
  
 El código siguiente genera el error C3704:  
  
```  
// C3704.cpp  
[ event_source(native) ]  
class CEventSrc {  
   public:  
      __event void fireEvent(int i, ...);   // C3704  
      // try the following line instead:  
      // __event void fireEvent(int i);  
};  
  
int main() {  
}  
```