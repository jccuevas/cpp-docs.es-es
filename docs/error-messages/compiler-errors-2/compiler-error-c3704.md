---
title: Error del compilador C3704 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3704
dev_langs: C++
helpviewer_keywords: C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae48bc886aab0211063cc7a9c2e73f3c7bbdd368
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3704"></a>Error del compilador C3704
'función': un método vararg no puede desencadenar eventos  
  
 Se intentó utilizar [__event](../../cpp/event.md) en un método vararg. Para corregir este error, reemplace la `fireEvent(int i, ...)` llama con el `fireEvent(int i)` llamar a como se muestra en el ejemplo de código siguiente.  
  
 El ejemplo siguiente genera C3704:  
  
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