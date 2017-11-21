---
title: Compilador advertencia (nivel 1) C4005 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4005
dev_langs: C++
helpviewer_keywords: C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 21023cf79a2ec25f94dc68cd3a55f722fa8316d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4005"></a>Compilador advertencia (nivel 1) C4005
'identificador': nueva definición de macro  
  
 El identificador de la macro se define dos veces. El compilador usa la segunda definición de macro.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Definir una macro en la línea de comandos y en el código con un `#define` directiva.  
  
2.  Macros importadas de archivos de inclusión.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones  
  
1.  Quite una de las definiciones.  
  
2.  Use un [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) Directiva antes de la segunda definición.  
  
 El ejemplo siguiente genera C4005:  
  
```  
// C4005.cpp  
// compile with: /W1 /EHsc  
#include <iostream>  
using namespace std;  
  
#define TEST "test1"  
#define TEST "test2"   // C4005 delete or rename to resolve the warning  
  
int main() {  
   cout << TEST << endl;  
}  
```