---
title: Error del compilador C2153 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2153
dev_langs: C++
helpviewer_keywords: C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1370e665708db783cf030c226de9de32c6c6b3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2153"></a>Error del compilador C2153
las constantes hexadecimales deben tener al menos un dígito hexadecimal  
  
 Las constantes hexadecimales 0 x, 0 X y \x no son válidos. Debe seguir al menos un dígito hexadecimal x o X.  
  
 El ejemplo siguiente genera C2153:  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```