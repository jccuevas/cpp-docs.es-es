---
title: Compilador advertencia (niveles 1 y 4) C4112 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6e82b2425aef840d8da7a0d0ad4dc4b81bd2a812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Advertencia del compilador (niveles 1 y 4) C4112
\#línea requiere un número entero entre 1 y número  
  
 La directiva [#line](../../preprocessor/hash-line-directive-c-cpp.md) especifica un parámetro entero que está fuera del intervalo permitido.  
  
 Si el parámetro especificado es menor que 1, el contador de línea se restablece en 1. Si el parámetro especificado es mayor que *número*, que es el límite definido por el compilador, el contador de línea no se modifica. Esta es una advertencia de nivel 1 con la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia de nivel 4 con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 El ejemplo siguiente genera la advertencia C4112:  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```