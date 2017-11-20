---
title: Error del compilador C2063 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2063
dev_langs: C++
helpviewer_keywords: C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 592303c26a8059898da6dc55d796de52bbb6b0a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2063"></a>Error del compilador C2063
'identificador': no es una función  
  
 El identificador se usa como función pero no se declara como función.  
  
 El ejemplo siguiente genera la advertencia C2063.  
  
```  
// C2063.c  
int main() {  
   int i, j;  
   j = i();    // C2063, i is not a function  
}  
```  
  
 Posible solución:  
  
```  
// C2063b.c  
int i() { return 0;}  
int main() {  
   int j;  
   j = i();  
}  
```