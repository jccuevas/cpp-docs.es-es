---
title: Error del compilador C2048 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2048
dev_langs: C++
helpviewer_keywords: C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18a724cd8d0e16b9440e1c4756b35cdf3f3c4821
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2048"></a>Error del compilador C2048
más de una etiqueta default  
  
 Una instrucción `switch` contiene varias etiquetas `default` . Elimine una de las etiquetas `default` para resolver el error.  
  
 El ejemplo siguiente genera la advertencia C2048:  
  
```  
// C2048.cpp  
int main() {  
   int a = 1;  
   switch (a) {  
      case 1:  
         a = 0;  
      default:  
         a = 2;  
      default:   // C2048  
         a = 3;  
   }  
}  
```  
  
 Posible resolución:  
  
```  
// C2048b.cpp  
int main() {  
   int a = 1;  
   switch (a) {  
      case 1:  
         a = 0;  
      default:  
         a = 2;  
   }  
}  
```