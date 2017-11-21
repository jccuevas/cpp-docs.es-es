---
title: Compilador advertencia (nivel 1) C4508 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4508
dev_langs: C++
helpviewer_keywords: C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d29e821fe29720b065bd9f003e1349c80bbb5c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4508"></a>Advertencia del compilador (nivel 1) C4508
'función': función debe devolver un valor; 'void' tipo de valor devuelto supone  
  
 La función no tiene especificado ningún tipo de valor devuelto. En este caso, también se desencadena C4430 y el compilador implementa la corrección indicada por C4430 (el valor predeterminado es de tipo int).  
  
 Para resolver esta advertencia, declare explícitamente el tipo de valor devuelto de funciones.  
  
 El ejemplo siguiente genera C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```