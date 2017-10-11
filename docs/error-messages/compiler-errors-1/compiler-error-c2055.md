---
title: C2055 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2055
dev_langs:
- C++
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c447d79179f3575230353b3db70717702b542b68
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2055"></a>C2055 de Error del compilador
se esperaba la lista de parámetros formales, no una lista de tipo  
  
 Una definición de función contiene una lista de tipo de parámetro en lugar de una lista de parámetros formales. ANSI C requiere que los parámetros formales asignarle un nombre a menos que sean void o un botón de puntos suspensivos (`...`).  
  
 El ejemplo siguiente genera C2055:  
  
```  
// C2055.c  
// compile with: /c  
void func(int, char) {}  // C2055  
void func (int i, char c) {}   // OK  
```
