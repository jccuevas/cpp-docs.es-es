---
title: Compilador advertencia (nivel 3) C4101 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4101
dev_langs: C++
helpviewer_keywords: C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: edd99402978a41a115afa2d96f86abd63d72afa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4101"></a>Compilador C4101 de advertencia (nivel 3)
'identificador': variable local sin referencia  
  
 Nunca se utiliza la variable local. Esta advertencia se produce en la siguiente situación:  
  
```  
// C4101a.cpp  
// compile with: /W3  
int main() {  
int i;   // C4101  
}  
```  
  
 Sin embargo, esta advertencia también se produce cuando se llama a un **estático** función miembro a través de una instancia de la clase:  
  
```  
// C4101b.cpp  
// compile with:  /W3  
struct S {  
   static int func()  
   {  
      return 1;  
   }  
};  
  
int main() {  
   S si;   // C4101, si is never used  
   int y = si.func();  
   return y;  
}  
```  
  
 En esta situación, el compilador utiliza información acerca de `si` para tener acceso a la **estático** función, pero la instancia de la clase no es necesaria para llamar a la **estático** función; por lo tanto, la advertencia. Para resolver esta advertencia, puede:  
  
-   Agregue un constructor, en el que el compilador utilizará la instancia de `si` en la llamada a `func`.  
  
-   Quitar el **estático** palabra clave de la definición de `func`.  
  
-   Llame a la **estático** función explícitamente: `int y = S::func();`.