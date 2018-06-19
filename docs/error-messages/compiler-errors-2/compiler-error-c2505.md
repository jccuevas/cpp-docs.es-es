---
title: Error del compilador C2505 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2505
dev_langs:
- C++
helpviewer_keywords:
- C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fac405fc13b7696f752ea6455dcbf464318dca56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227666"
---
# <a name="compiler-error-c2505"></a>Error del compilador C2505
'símbolo': '__declspec (modifer)' solo puede aplicarse a las declaraciones o definiciones de objetos globales o miembros de datos estáticos  
  
 Un `__declspec` modificador que está diseñado para usarse solo en el ámbito global se usó en una función.  
  
 Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).  
  
 El ejemplo siguiente genera C2505:  
  
```  
// C2505.cpp  
// compile with: /clr  
  
// OK  
__declspec(process) int ii;  
__declspec(appdomain) int jj;  
  
int main() {  
   __declspec(process) int i;   // C2505  
   __declspec(appdomain) int j;   // C2505  
}  
```