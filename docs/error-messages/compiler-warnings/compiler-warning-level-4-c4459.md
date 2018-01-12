---
title: Compilador advertencia (nivel 4) C4459 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4459
dev_langs: C++
helpviewer_keywords: C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47380915dd18387fa3cc2af54d42a3777aab3f5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4459"></a>Compilador advertencia (nivel 4) C4459
  
> declaración de '*identificador*' oculta la declaración global
  
La declaración de *identificador* en el ámbito local oculta la declaración de idéntico nombre *identificador* en el ámbito global. Esta advertencia le permite saber que las referencias a *identificador* en este ámbito resolver en la versión declarada localmente, no la versión global, que puede ser o no su intención. Por lo general, se recomienda que minimice el uso de variables globales como una buena práctica de ingeniería. Para minimizar la contaminación de espacio de nombres global, se recomienda el uso de un espacio de nombres para las variables globales.  
  
Esta advertencia era nueva en Visual Studio 2015, en Visual C++ versión del compilador 18.00. Para suprimir las advertencias de esa versión del compilador o posteriormente durante la migración del código, utilice la [/Wv:18](../../build/reference/compiler-option-warning-level.md) opción del compilador. 

## <a name="example"></a>Ejemplo
  
 El ejemplo siguiente genera C4459:  
  
```cpp  
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() { 
    int global_or_local; // warning C4459 
    global_or_local = 2;
} 
```  
  
Una manera de solucionar este problema consiste en crear un espacio de nombres para las campos globales, pero no usar un `using` nombres completos de directiva para devolver ese espacio de nombres en el ámbito, por lo que todas las referencias deben utilizar el ambiguo:  
  
```cpp  
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() { 
    int global_or_local; // OK 
    global_or_local = 2;
    globals::global_or_local = 3;
} 
```  
