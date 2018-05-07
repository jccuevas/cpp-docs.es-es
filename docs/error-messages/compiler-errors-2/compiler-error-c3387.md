---
title: Error del compilador C3387 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3387
dev_langs:
- C++
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5469088b6707faa31e1d49157dcbc9991ffb7060
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3387"></a>Error del compilador C3387
'member': __declspec (dllexport) /\__declspec (dllimport) no se puede aplicar a un miembro de una clase administrada o tipo WinRT  
  
 El `dllimport` y [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modificadores no son válidos en miembros de una clase administrada o de tipo en tiempo de ejecución de Windows.  
  
 El ejemplo siguiente genera el error C3387 y muestra cómo corregirlo:  
  
```  
// C3387a.cpp  
// compile with: /clr /c  
ref class X2 {  
   void __declspec(dllexport) mf() {   // C3387  
   // try the following line instead  
   // void mf() {  
   }  
};  
```