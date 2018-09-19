---
title: Advertencia de la línea de comandos D9041 | Microsoft Docs
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
ms.openlocfilehash: 70bf82cfdca787898a02fb52926981bfd1a1b3e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033386"
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