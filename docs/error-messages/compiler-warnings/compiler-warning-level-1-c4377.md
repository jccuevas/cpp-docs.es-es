---
title: Compilador advertencia (nivel 1) C4377 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef049f85cd17bfeaba243b84da9fca93ae4036b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4377"></a>Advertencia del compilador (nivel 1) C4377
los tipos nativos son privados de forma predeterminada; -d1PrivateNativeTypes está en desuso  
  
 En versiones anteriores, los tipos nativos en ensamblados eran públicos de forma predeterminada y una opción de compilador interno y no documentada (**/d1PrivateNativeTypes**) se usa para hacer que sean privadas.  
  
 Todos los tipos, nativos y CLR, ahora son privados de forma predeterminada en un ensamblado, por lo que **/d1PrivateNativeTypes** ya no es necesario.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4377.  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```