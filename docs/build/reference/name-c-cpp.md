---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: c4888b8f9b6dba4b826f2ee7dda7529a4bdf1586
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414504"
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
