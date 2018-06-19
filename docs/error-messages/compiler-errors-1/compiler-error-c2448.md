---
title: Error del compilador C2448 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2448
dev_langs:
- C++
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc62d7aeba0a128c9b736586e6c1502227de717
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226054"
---
# <a name="compiler-error-c2448"></a>Error del compilador C2448
'identificador': inicializador de estilo de función parece ser una definición de función  
  
 La definición de función es incorrecta.  
  
 Este error puede deberse a una lista formal del lenguaje C de estilo antiguo.  
  
 El ejemplo siguiente genera C2448:  
  
```  
// C2448.cpp  
void func(c)  
   int c;  
{}   // C2448  
```