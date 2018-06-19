---
title: Error del compilador C3865 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99a872d4cf7ed285a0798461c77adf904cfa3e71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275504"
---
# <a name="compiler-error-c3865"></a>Error del compilador C3865
'convención de llamada': solo puede usarse en funciones miembro nativas  
  
 Se usó una convención de llamada en una función que era una función global o en una función miembro administrada. La convención de llamada solo puede usarse en una función miembro (no administrado) nativo.  
  
 Para obtener más información, consulte [convenciones de llamada](../../cpp/calling-conventions.md).  
  
 El ejemplo siguiente genera C3865:  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```