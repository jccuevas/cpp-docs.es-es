---
title: Compilador advertencia (nivel 1) C4329 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4329
dev_langs:
- C++
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7eca757f361acaa0aeaf90332d33400f5a0ba6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4329"></a>Advertencia del compilador (nivel 1) C4329
__declspec(Align()) se omite en enum  
  
 El uso de la [alinear](../../cpp/align-cpp.md) palabra clave de la [__declspec](../../cpp/declspec.md) modificador no está permitido en un `enum`. El ejemplo siguiente genera C4329:  
  
```  
// C4329.cpp  
// compile with: /W1 /LD  
enum __declspec(align(256)) TestEnum {   // C4329  
   TESTVAL1,  
   TESTVAL2,  
   TESTVAL3  
};  
__declspec(align(256)) enum TestEnum1;  
```