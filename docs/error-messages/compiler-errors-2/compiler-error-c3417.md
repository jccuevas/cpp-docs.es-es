---
title: Error del compilador C3417 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3417
dev_langs:
- C++
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b83c3b6cf5697ca2e52f9f8ad6afdc2754edd4f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256423"
---
# <a name="compiler-error-c3417"></a>Error del compilador C3417
'member': tipos de valor no pueden contener funciones miembro especiales definidas por el usuario  
  
 Tipos de valor no pueden contener funciones como un constructor de instancia predeterminado, un destructor o un constructor de copias.  
  
 El ejemplo siguiente genera C3517:  
  
```  
// C3417.cpp  
// compile with: /clr /c  
value class VC {  
   VC(){}   // C3417  
  
   // OK  
   static VC(){}  
   VC(int i){}  
};  
```