---
title: Compilador advertencia (nivel 1) C4326 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4326
dev_langs: C++
helpviewer_keywords: C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6a7c0e412b733e451ab3147a726c37a43241e1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4326"></a>Advertencia del compilador (nivel 1) C4326
tipo de valor devuelto de 'function' debe ser 'type1' en lugar de 'tipo2'  
  
 Una función ha devuelto un tipo distinto de ***type1***. Por ejemplo, si se usa [/Za](../../build/reference/za-ze-disable-language-extensions.md), main no devuelve un `int`.  
  
 El ejemplo siguiente genera C4326:  
  
```  
// C4326.cpp  
// compile with: /Za /W1  
char main()  
{   // C4326 try int main  
}  
```