---
title: Compilador advertencia (nivel 1) C4142 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c87b7689cf11ab28c1a6377ff85e1594fd1b5fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284438"
---
# <a name="compiler-warning-level-1-c4142"></a>Compilador advertencia (nivel 1) C4142
benigno nueva definición de tipo  
  
 Se vuelve a definir un tipo de forma que no tiene ningún efecto en el código generado.  
  
 Posibles causas del error:  
  
-   Una función miembro de una clase derivada tiene un tipo de valor devuelto diferente de la función miembro correspondiente de la clase base.  
  
-   Un tipo definido con el `typedef` comando se vuelve a definir usando una sintaxis diferente.  
  
 El ejemplo siguiente genera C4142:  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```