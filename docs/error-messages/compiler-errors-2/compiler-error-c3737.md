---
title: Error del compilador C3737 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3737
dev_langs: C++
helpviewer_keywords: C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af179d622ffe8354352cc6b87ab009b825e55b36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3737"></a>Error del compilador C3737
'delegado': un delegado no puede tener una convención de llamada explícita  
  
 No se puede especificar el [convención de llamada](../../cpp/calling-conventions.md) para un `delegate`.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C3737:  
  
```  
// C3737a.cpp  
// compile with: /clr  
delegate void __stdcall MyFunc();   // C3737  
// Try the following line instead.  
// delegate void MyFunc();  
  
int main() {  
}  
```  
