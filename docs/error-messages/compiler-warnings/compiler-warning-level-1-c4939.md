---
title: Compilador advertencia (nivel 1) C4939 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4939
dev_langs:
- C++
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 459674bb4e6899563a18943f7ba510a6168d0e28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296889"
---
# <a name="compiler-warning-level-1-c4939"></a>Advertencia del compilador (nivel 1) C4939
\#pragma vtordisp está en desuso y se quitará en una futura versión de Visual C++  
  
 Se quitará la pragma [vtordisp](../../preprocessor/vtordisp.md) en próximas versiones de Visual C++  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4939:  
  
```  
// C4939.cpp  
// compile with: /c /W1  
#pragma vtordisp(off)   // C4939  
```