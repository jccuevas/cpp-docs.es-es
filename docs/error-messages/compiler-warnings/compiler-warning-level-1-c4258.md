---
title: Compilador advertencia (nivel 1) C4258 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 436ef3dd9984750885390a3974572b9d86bd7243
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4258"></a>Advertencia del compilador (nivel 1) C4258
'variable': definición de la de bucle se pasa por alto; se utiliza la definición de ámbito de inclusión"  
  
 En [/Ze](../../build/reference/za-ze-disable-language-extensions.md) y [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), las variables definidas en un [para](../../cpp/for-statement-cpp.md) bucle salga del ámbito después de la **para** termina un bucle. Esta advertencia se produce si una variable con el mismo nombre que la variable de bucle, pero definida en el bucle envolvente se vuelve a usar en el ámbito que contiene el **para** bucle. Por ejemplo:  
  
```  
// C4258.cpp  
// compile with: /Zc:forScope /W1  
int main()  
{  
   int i;  
   {  
      for (int i =0; i < 1; i++)  
         ;  
      i = 20;   // C4258 i (in for loop) has gone out of scope  
   }  
}  
```