---
title: Error del compilador C2381 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2381
dev_langs:
- C++
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd5f5edcf95144333524c41b803c24b728a621f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2381"></a>Error del compilador C2381
'función': nueva definición; __declspec (noreturn) es diferente  
  
 Una función se declaran y se definen a continuación, pero la definición se usa el [noreturn](../../cpp/noreturn.md) `__declspec` modificador. El uso de `noreturn` constituye una nueva definición de la función; la declaración y la definición deben coincidir en el uso de `noreturn`.  
  
 El ejemplo siguiente genera C2381:  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```