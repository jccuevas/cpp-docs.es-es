---
title: Error del compilador C3910 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3910
dev_langs:
- C++
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: faa2060baedeb8ce26f153109b808603d8c576d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3910"></a>Error del compilador C3910
'evento': debe definir el miembro 'método'  
  
 Un evento se ha definido, pero no contiene el método de descriptor de acceso necesario especificado.  
  
 Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3910:  
  
```  
// C3910.cpp  
// compile with: /clr /c  
delegate void H();  
ref class X {  
   event H^ E {  
      // uncomment the following lines  
      // void add(H^) {}  
      // void remove( H^ h ) {}  
      // void raise( ) {}  
   };   // C3910  
  
   event H^ E2; // OK data member  
};  
```