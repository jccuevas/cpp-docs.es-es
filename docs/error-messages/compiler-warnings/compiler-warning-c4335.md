---
title: Advertencia del compilador C4335 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: dc8436664038d3f53f3a01d5006c41c3d0e4c8f0
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-c4335"></a>Advertencia del compilador C4335
Formato de archivo Mac detectado: convierta el archivo de código fuente en formato DOS o UNIX  
  
 El carácter de terminación de la línea de la primera línea de un archivo de origen es el estilo de Macintosh ('\r') en lugar de UNIX ('\n') o DOS ('\r\n').  
  
 Esta advertencia siempre se emite como un error.  Vea [advertencia](../../preprocessor/warning.md) pragma para obtener información acerca de cómo deshabilitar esta advertencia.  Además, esta advertencia solo se emite una vez por cada operación de compilación. Por lo tanto, si hay varias `#include` directivas que especifican los archivos en formato Macintosh, C4335 solo se emitirá una vez.  
  
 Una manera de generar archivos en formato Macintosh es mediante el uso de la **opciones avanzadas para guardar** (en el **archivo** menú) en Visual Studio.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4335.  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```
