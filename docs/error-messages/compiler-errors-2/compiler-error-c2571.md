---
title: Error del compilador C2571 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2571
dev_langs: C++
helpviewer_keywords: C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8bfb4f9af849efea2fa3aa8a84a57f1cfb4cd502
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2571"></a>Error del compilador C2571
'función': función virtual no puede estar en la unión 'unión'  
  
 Se declara una unión con una función virtual. Puede declarar una función virtual solo en una clase o estructura.  Soluciones posibles:  
  
1.  Cambie la unión a una clase o estructura.  
  
2.  Hacer que la función no virtual.  
  
 El ejemplo siguiente genera C2571:  
  
```  
// C2571.cpp  
// compile with: /c  
union A {  
   virtual void func1();   // C2571  
   void func2();   // OK  
};  
```