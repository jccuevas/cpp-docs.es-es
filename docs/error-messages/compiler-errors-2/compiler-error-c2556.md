---
title: Error del compilador C2556 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2556
dev_langs: C++
helpviewer_keywords: C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17b04008d5ee6676cb7c8060dd9369274cbe01ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2556"></a>Error del compilador C2556
'identificador': las funciones sobrecargadas sólo se diferencian por el tipo de valor devuelto  
  
 Las funciones sobrecargadas tienen diferentes tipos de valor devuelto pero la misma lista de parámetros. Cada función sobrecargada debe tener una lista de parámetros formales distinta.  
  
 El ejemplo siguiente genera C2556:  
  
```  
// C2556.cpp  
// compile with: /c  
class C {  
   int func();  
   double func();   // C2556  
   int func(int i);   // ok parameter lists differ  
};  
```