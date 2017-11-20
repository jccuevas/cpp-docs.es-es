---
title: -LINENUMBERS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /linenumbers
dev_langs: C++
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f81ee61dacab794d457db88532025c05ae5d413b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linenumbers"></a>/LINENUMBERS
```  
/LINENUMBERS  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta opción muestra los números de línea COFF. Números de línea no existan en un archivo de objeto si se compiló con el programa de base de datos (/Zi), compatible con C7 (/ Z7), o sólo números de línea (/ Zd). Un archivo ejecutable o DLL contiene números de línea COFF si se vincula con generar información de depuración (/Debug).  
  
 Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)