---
title: Advertencia de la línea de comandos D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196580"
---
# <a name="command-line-warning-d9041"></a>Advertencia de la línea de comandos D9041

valor no válido ' value ' para '/option '; se supone ' valor '; Agregar "/Analyze" a las opciones de línea de comandos al especificar esta advertencia

Se ha agregado un número de advertencia de análisis de código a la opción de línea de comandos **/WD**, **/We**, **/WO**o **/WL** sin especificar también la opción de línea de comandos **/Analyze** . Para solucionar este error, agregue la opción de línea de comandos **/Analyze** o quite el número de advertencia no válido de la opción de línea de comandos **/w** adecuada.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo de línea de comandos se genera la advertencia D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Para corregir la advertencia, agregue la opción de línea de comandos **/Analyze** . Si no se admite **/Analyze** en su versión del compilador, quite el número de advertencia no válido de la opción **/WD** .

## <a name="see-also"></a>Consulte también

[Errores de la línea de comandos de D8000 a D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Opciones del compilador de MSVC](../../build/reference/compiler-options.md)
