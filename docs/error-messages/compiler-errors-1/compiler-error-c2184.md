---
title: Error del compilador C2184 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2184
dev_langs: C++
helpviewer_keywords: C2184
ms.assetid: 80fc8bff-7d76-4bde-94d2-01d84bb6824a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e5402835be51b67bece4853996f281cf0ab5cfb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2184"></a>Error del compilador C2184
'type': tipo no válido para la expresión __except, debe ser un entero.  
  
 Se usó un tipo en una instrucción [__except](../../c-language/try-except-statement-c.md) , pero el tipo no está permitido.  
  
 El ejemplo siguiente genera la advertencia C2184:  
  
```  
// C2184.cpp  
void f() {  
   int * p;  
   __try{}  
   __except(p){};   // C2184  
}  
```  
  
 Posible resolución:  
  
```  
// C2184b.cpp  
// compile with: /c  
void f() {  
   int i = 0;  
   __try{}  
   __except(i){};  
}  
```