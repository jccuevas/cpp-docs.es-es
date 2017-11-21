---
title: Compilador advertencia (nivel 2) C4307 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4307
dev_langs: C++
helpviewer_keywords: C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 31a17a5130bf8068928ba5840f792fca54e45cf2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4307"></a>Advertencia del compilador (nivel 2) C4307
'operador': desbordamiento de constante integral  
  
 Este operador se usa en una expresión que da como resultado una constante entera que desborda el espacio asignado para él. Debe usar un tipo mayor para la constante. A **firmado int** contiene un valor más pequeño que un `unsigned int` porque el **firmado int** utiliza un bit para representar el inicio de sesión.  
  
 El ejemplo siguiente genera C4307:  
  
```  
// C4307.cpp  
// compile with: /W2  
int i = 2000000000 + 2000000000;   // C4307  
int j = (unsigned)2000000000 + 2000000000;   // OK  
  
int main()  
{  
}  
```