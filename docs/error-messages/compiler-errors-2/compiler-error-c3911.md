---
title: Error del compilador C3911 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3911
dev_langs:
- C++
helpviewer_keywords:
- C3911
ms.assetid: b786da59-0e99-479d-bc0d-551126e940f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfff502e5dc4a9628f11fbcd46129646ed720ea6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274019"
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