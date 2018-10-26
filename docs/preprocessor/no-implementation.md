---
title: no_implementation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f169b30394e3fdf893475a49946266143772eb7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078068"
---
# <a name="noimplementation"></a>no_implementation
**Específicos de C++**

Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.

## <a name="syntax"></a>Sintaxis

```
no_implementation
```

## <a name="remarks"></a>Comentarios

Si se especifica este atributo, el encabezado.tlh, con las declaraciones para exponer elementos de la biblioteca de tipos, se generará sin una instrucción `#include` para incluir el archivo de encabezado .tli.

Este atributo se utiliza junto con [implementation_only](../preprocessor/implementation-only.md).

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)