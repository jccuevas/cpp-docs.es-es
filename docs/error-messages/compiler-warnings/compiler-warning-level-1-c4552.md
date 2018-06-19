---
title: Compilador advertencia (nivel 1) C4552 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4552
dev_langs:
- C++
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b58d33286163050db533fed00d27abe8903e9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281133"
---
# <a name="compiler-warning-level-1-c4552"></a>Advertencia del compilador (nivel 1) C4552
'operador': operador no tiene ningún efecto; se esperaba un operador con efectos secundarios  
  
 Si una instrucción de expresión tiene un operador con ningún efecto secundario como la parte superior de la expresión, probablemente es un error.  
  
 Para evitar esta advertencia, coloque la expresión entre paréntesis.  
  
 El ejemplo siguiente genera C4552:  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```