---
title: Error del compilador C3295 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3295
dev_langs: C++
helpviewer_keywords: C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b72e4839341006d2058c21a1523b0d7567f51696
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3295"></a>Error del compilador C3295
'#pragma pragma' solo se puede usar en un ámbito global o de espacio de nombres  
  
 Algunas pragmas no se pueden usar en una función.  Vea [directivas Pragma y la palabra clave __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3295.  
  
```  
// C3295.cpp  
int main() {  
   #pragma managed   // C3295  
}  
```