---
title: Error del compilador C2459 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2459
dev_langs:
- C++
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6013720b55892ffd34e1faf132a69842e4bceb50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2459"></a>Error del compilador C2459
'identificador': se está definiendo; no se puede agregar como miembro anónimo  
  
 Una clase, estructura o unión se vuelve a definir en su propio ámbito por un miembro de una unión anónima.  
  
 El ejemplo siguiente genera C2459:  
  
```  
// C2459.cpp  
// compile with: /c  
class C {  
   union { int C; };   // C2459  
   union { int D; };  
};  
```