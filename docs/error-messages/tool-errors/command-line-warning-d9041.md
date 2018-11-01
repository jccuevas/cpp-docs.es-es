---
title: Advertencia de la línea de comandos D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 79bdafcd4ed6af061b9c0ee27aae6eed6bc981a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513924"
---
# <a name="command-line-warning-d9041"></a>Advertencia de la línea de comandos D9041

valor no válido 'value' para '/ option'; Suponiendo que 'valor'; Agregue ' / analyze' a las opciones de línea de comandos cuando especifique esta advertencia

Un número de advertencia de análisis de código se agregó a la **/wd**, **/we**, **/wo**, o **/wl** opción de línea de comandos sin especificar también el **/ analyze** opción de línea de comandos. Para solucionar este error, agregue el **/ analyze** opción de línea de comandos, o quitar el número de advertencia no válido con la correspondiente **/w** opción de línea de comandos.

## <a name="example"></a>Ejemplo

El ejemplo de línea de comandos siguiente genera la advertencia D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Para corregir la advertencia, agregue el **/ analyze** opción de línea de comandos. Si **/ analyze** no es se admite en la versión del compilador, quite el número de advertencia no válido desde el **/wd** opción.

## <a name="see-also"></a>Vea también

[Errores de la línea de comandos de D8000 a D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)