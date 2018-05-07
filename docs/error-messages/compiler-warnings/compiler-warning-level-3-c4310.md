---
title: Compilador advertencia (nivel 3) C4310 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4310
dev_langs:
- C++
helpviewer_keywords:
- C4310
ms.assetid: cba3eca1-f1ed-499c-9243-337446bdbdd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd3ab8ba6eb9175ad3f567408faa1f78c09a6f6a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4310"></a>Advertencia del compilador (nivel 3) C4310
la conversión trunca el valor constante  
  
 Un valor constante se convierte en un tipo más pequeño. El compilador realiza la conversión, lo cual trunca los datos. El ejemplo siguiente genera C4310:  
  
```  
// C4310.cpp  
// compile with: /W4  
int main() {  
   long int a;  
   a = (char) 128;   // C4310, use value 0-127 to resolve  
}  
```