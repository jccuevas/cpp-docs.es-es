---
title: NAME (C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: d0813befc622db72e095c449794405fc5d58465b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320583"
---
# <a name="name-cc"></a>NAME (C/C++)

Especifica un nombre para el archivo de salida principal.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>Comentarios

Es una manera equivalente para especificar un nombre de archivo de salida con el [/OUT](out-output-file-name.md) opción del vinculador y una manera equivalente a establecer la dirección base es con la [/base](base-base-address.md) opción del vinculador. Si se especifican ambos, / OUT invalida **nombre**.

Si compila un archivo DLL, nombre sólo afectará el nombre del archivo DLL.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
