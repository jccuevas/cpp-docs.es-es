---
title: Error del compilador C2390 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2390
dev_langs: C++
helpviewer_keywords: C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 37803b8eb5034fb3281dcea385b4a0fca462aaf0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2390"></a>Error del compilador C2390
'identificador': clase de almacenamiento incorrecta 'especificador'  
  
 La clase de almacenamiento no es válida para el identificador de ámbito global. La clase de almacenamiento predeterminada se utiliza en lugar de la clase no válida.  
  
 Soluciones posibles:  
  
-   Si el identificador es una función, declárelo con `extern` almacenamiento.  
  
-   Si el identificador es un parámetro formal o una variable local, declárelo con almacenamiento automático.  
  
-   Si el identificador es una variable global, declárelo con ninguna clase de almacenamiento (almacenamiento automático).  
  
## <a name="example"></a>Ejemplo  
  
-   El ejemplo siguiente genera C2390:  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```