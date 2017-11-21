---
title: Compilador advertencia (nivel 1) C4224 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4224
dev_langs: C++
helpviewer_keywords: C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b354a8d2cf3b4a12e81b22521cd75cbb0414f996
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4224"></a>Advertencia del compilador (nivel 1) C4224
ha utilizado una extensión no estándar: el parámetro formal 'identificador' se definió anteriormente como un tipo  
  
 El identificador se utilizó anteriormente como un `typedef`. Esto da lugar a una advertencia en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4224.cpp  
// compile with: /Za /W1 /LD  
typedef int I;  
void func ( int I );  // C4224  
```