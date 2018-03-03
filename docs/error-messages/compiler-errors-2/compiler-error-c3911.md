---
title: Error del compilador C3911 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3911
dev_langs:
- C++
helpviewer_keywords:
- C3911
ms.assetid: b786da59-0e99-479d-bc0d-551126e940f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c6da599d3665541319e21273d9f6daedd82a2a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3911"></a>Error del compilador C3911
'event_accessor_method': función debe tener un tipo 'firma'  
  
 Método de descriptor de acceso de un evento no se ha declarado correctamente.  
  
 Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3911:  
  
```  
// C3911.cpp  
// compile with: /clr  
using namespace System;  
delegate void H(String^, int);  
  
ref class X {  
   event H^ E1 {  
      void add() {}   // C3911  
      // try the following line instead  
      // void add(H ^ h) {}  
  
      void remove(){}  
      // try the following line instead  
      // void remove(H ^ h) {}  
  
      void raise(){}  
      // try the following line instead  
      // void raise(String ^ s, int i) {}  
   };  
};  
```