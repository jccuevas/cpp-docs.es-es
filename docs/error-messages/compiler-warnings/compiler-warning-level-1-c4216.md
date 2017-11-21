---
title: Compilador advertencia (nivel 1) C4216 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4216
dev_langs: C++
helpviewer_keywords: C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 02f43c2dda11b765becf0b9244a0887a99df9b33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4216"></a>Advertencia del compilador (nivel 1) C4216
ha utilizado una extensión no estándar: float long  
  
 Las extensiones de Microsoft predeterminadas (/Ze) tratan **float long** como **doble**. La compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) no lo hace. Use **doble** para mantener la compatibilidad. El ejemplo siguiente genera C4216:  
  
```  
// C4216.cpp  
// compile with: /W1  
float long a;   // C4216  
  
// use the line below to resolve the warning  
// double a;  
  
int main() {  
}  
```