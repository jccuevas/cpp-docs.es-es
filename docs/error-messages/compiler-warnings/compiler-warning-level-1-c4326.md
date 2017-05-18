---
title: Compilador (nivel 1) de advertencia C4326 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 08919a46a9f48ef42849351f19099c339b15ed90
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4326"></a>Advertencia del compilador (nivel 1) C4326
tipo de valor devuelto de 'función' debe ser 'tipo1' en lugar de 'tipo2'  
  
 Una función ha devuelto un tipo distinto de ***type1***. Por ejemplo, mediante [/Za](../../build/reference/za-ze-disable-language-extensions.md), main no devuelve un `int`.  
  
 El ejemplo siguiente genera C4326:  
  
```  
// C4326.cpp  
// compile with: /Za /W1  
char main()  
{   // C4326 try int main  
}  
```
