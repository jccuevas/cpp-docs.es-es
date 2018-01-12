---
title: Error del compilador C3851 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3851
dev_langs: C++
helpviewer_keywords: C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c5f0cca8f3c1dfc4b3b35d494ebf73459a74d03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3851"></a>Error del compilador C3851
'char': un nombre de carácter universal no puede designar un carácter en el juego de caracteres básico  
  
 En código compilado como C++, no se puede usar un nombre de carácter universal que representa un carácter del juego básico de caracteres de código fuente fuera un literal de cadena o carácter. Para obtener más información, vea [Character Sets](../../cpp/character-sets2.md). En código compilado como C, no se puede usar un nombre de carácter universal para los caracteres del rango de 0x2 a 0x7f, inclusive, excepto 0x24 ('$'), 0x40 ('@') o 0x60 ('`').  
  
 En los ejemplos siguientes se genera el error C3851 y se muestra cómo corregirlo:  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```