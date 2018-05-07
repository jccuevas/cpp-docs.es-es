---
title: Error del compilador C2504 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2504
dev_langs:
- C++
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bac0f8f28955af172590535568289182c3489d6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2504"></a>Error del compilador C2504
'clase': clase base sin definir  
  
 La clase base se declara, pero nunca se ha definido.  Causas posibles:  
  
1.  Falta el archivo de inclusión.  
  
2.  La clase base externa no se declara con [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
 El ejemplo siguiente genera C2504:  
  
```  
// C2504.cpp  
// compile with: /c  
class A;  
class B : public A {};   // C2504  
```  
  
 VALE  
  
```  
class C{};  
class D : public C {};  
```