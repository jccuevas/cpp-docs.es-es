---
title: Compilador advertencia (nivel 1) C4129 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4129
dev_langs: C++
helpviewer_keywords: C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1efeca1e597af8e7f96b2854fcbcfc49b000009a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4129"></a>Compilador advertencia (nivel 1) C4129
'carácter': secuencia de escape de carácter no reconocida  
  
 El `character` después de una barra diagonal inversa (\\) en un carácter o cadena constante no se reconoce como una secuencia de escape válida. La barra diagonal inversa se omite y no se imprimen. El carácter que sigue a la barra diagonal inversa se imprime.  
  
 Para imprimir una única barra diagonal inversa, especifique una barra diagonal inversa doble (\\\\).  
  
 El estándar de C++, en la sección 2.13.2 se describen las secuencias de escape.  
  
 El ejemplo siguiente genera C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```