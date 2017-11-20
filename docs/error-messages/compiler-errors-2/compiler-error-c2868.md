---
title: Error del compilador C2868 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2868
dev_langs: C++
helpviewer_keywords: C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 62c8ea961db2547976e39a8873542a9f85dc4be7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2868"></a>Error del compilador C2868  
  
> '*identificador*': sintaxis no válida para la declaración using; esperado nombre completo  
  
A [mediante declaración](../../cpp/using-declaration.md) requiere un *nombre completo*, un operador de ámbito (`::`) separados de la secuencia de nombres de espacio de nombres, clase o enumeración que termina con el nombre del identificador. Un operador de resolución de ámbito único puede utilizarse para introducir un nombre de espacio de nombres global.  
  
## <a name="example"></a>Ejemplo  
  
El ejemplo siguiente genera C2868 y también muestra el uso correcto:  
  
```cpp  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```