---
title: Compilador advertencia (nivel 1) C4377 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4377
dev_langs: C++
helpviewer_keywords: C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b2cf61aa35bcfc40a40febb9e066caba6decd682
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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