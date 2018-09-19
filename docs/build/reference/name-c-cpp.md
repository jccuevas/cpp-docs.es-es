---
title: NOMBRE (C O C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715759"
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