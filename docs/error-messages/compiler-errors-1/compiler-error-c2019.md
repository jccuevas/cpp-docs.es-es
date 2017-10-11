---
title: C2019 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2019
dev_langs:
- C++
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 93c91bccf1b9bc709d006696b22e0e8c2febb713
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2019"></a>C2019 de Error del compilador
se esperaba una directiva del preprocesador; se encontró 'carácter'  
  
 El carácter seguido de un `#` inicio de sesión, pero no es la primera letra de una directiva de preprocesador.  
  
 El ejemplo siguiente genera C2019:  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 Posible solución:  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```
