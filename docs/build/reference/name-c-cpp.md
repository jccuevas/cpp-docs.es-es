---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c05e82409d6b6e48390d54160e8ff23ada788d41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646204"
---
# <a name="name-cc"></a>NAME (C/C++)

Especifica un nombre para el archivo de salida principal.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Comentarios

Es una manera equivalente para especificar un nombre de archivo de salida con el [/OUT](../../build/reference/out-output-file-name.md) opción del vinculador y una manera equivalente a establecer la dirección base es con la [/base](../../build/reference/base-base-address.md) opción del vinculador. Si se especifican ambos, / OUT invalida **nombre**.

Si compila un archivo DLL, nombre sólo afectará el nombre del archivo DLL.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)