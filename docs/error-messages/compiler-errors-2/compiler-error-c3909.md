---
title: Error del compilador C3909 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53e89dd422b1289d926ab04a0f17ae4d6185d19d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270822"
---
# <a name="compiler-error-c3909"></a>Error del compilador C3909
aWinRT o declaración de evento administrado debe aparecer en un tipo administrado o WinRT  
  
 Se declaró un evento de Windows Runtime o administrado en un tipo nativo. Para corregir este error, declare los eventos en tipos de Windows Runtime o en tipos administrados.  
  
 Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C3909 y muestra cómo corregirlo:  
  
```  
// C3909.cpp  
// compile with: /clr /c  
delegate void H();  
class X {  
   event H^ E;   // C3909 - use ref class X instead  
};  
  
ref class Y {  
   static event H^ E {  
      void add(H^) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```