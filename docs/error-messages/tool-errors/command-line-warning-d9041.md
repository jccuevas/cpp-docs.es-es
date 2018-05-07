---
title: Línea de comandos D9041 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c22573d26e09e14789f4cbd64d68f4082125c2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9041"></a>Advertencia de la línea de comandos D9041
valor no válido 'value' para '/ option'; se supone 'valor'; Agregue ' / analyze' a las opciones de línea de comandos cuando se especifica esta advertencia  
  
 Un número de advertencia de análisis de código se agrega a la **/wd**, **/we**, **/wo**, o **/wl** opción de línea de comandos sin especificar también el **/ analyze** opción de línea de comandos. Para solucionar este error, agregue el **/ analyze** opción de línea de comandos, o quitar el número de advertencia no válido con la correspondiente **/w** opción de línea de comandos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de línea de comandos siguiente se genera la advertencia D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 Para corregir la advertencia, agregue el **/ analyze** opción de línea de comandos. Si **/ analyze** no es compatible con la versión del compilador, quite el número de advertencia no válido de la **/wd** opción.  
  
## <a name="see-also"></a>Vea también  
 [Errores de línea de comandos de D8000 a través de D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)