---
title: Error del compilador C2472 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2472
dev_langs: C++
helpviewer_keywords: C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed41a3d78ab9652d1e88ceefe29011eb5b2225a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2472"></a>Error del compilador C2472
'function' no se puede generar en código administrado: 'message'; compile con /clr para generar una imagen mixta  
  
 Este error se producirá cuando se usen tipos no admitidos por código administrado en un entorno puro de Common Language Runtime (CLR). Compile con **/clr** para resolver el error.  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2472.  
  
```  
// C2472.cpp  
// compile with: /clr:pure  
// C2472 expected  
  
#include <cstdlib>  
  
int main()  
{  
   int * __ptr32 p32;  
   int * __ptr64 p64;  
  
   p32 = (int * __ptr32)malloc(4);  
   p64 = p32;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [/CLR (compilación de common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)