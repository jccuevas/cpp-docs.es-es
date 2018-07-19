---
title: Error del compilador C2879 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2879
dev_langs:
- C++
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba1738da7d349ecafd9f10f31d8f05ac1f12df0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243168"
---
# <a name="compiler-error-c2879"></a>Error del compilador C2879
'símbolo': sólo un espacio de nombres existente se puede proporcionar un nombre alternativo mediante una definición de alias de espacio de nombres  
  
 No se puede crear un [alias de espacio de nombres](../../cpp/namespaces-cpp.md#namespace_aliases) un símbolo que no sea un espacio de nombres.  
  
 El ejemplo siguiente genera C2879:  
  
```  
// C2879.cpp  
int main() {  
   int i;  
   namespace A = i;   // C2879 i is not a namespace  
}  
```