---
title: Error del compilador C2042 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2042
dev_langs:
- C++
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5b0442371b210f40d58a10b6bf1107979ea88db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2042"></a>Error del compilador C2042
las palabras clave signed/unsigned se excluyen mutuamente  
  
 Las palabras clave `signed` y `unsigned` se usan en una sola declaración.  
  
 El ejemplo siguiente genera la advertencia C2042.  
  
```  
// C2042.cpp  
unsigned signed int i;   // C2042  
```  
  
 Posible resolución:  
  
```  
// C2042b.cpp  
// compile with: /c  
unsigned int i;  
signed int ii;  
```