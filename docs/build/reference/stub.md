---
title: CÓDIGO AUXILIAR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151d7b425a7f397a05e3a06e9d94489a0c76f899
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725119"
---
# <a name="stub"></a>STUB

Cuando se utiliza en un archivo de definición de módulo que genera un controlador de dispositivo virtual (VxD), le permite especificar un nombre de archivo que contiene una estructura IMAGE_DOS_HEADER (definida en WINNT. H) que se usará en el controlador de dispositivo virtual (VxD), en lugar del encabezado predeterminado.

```
STUB:filename
```

## <a name="remarks"></a>Comentarios

Una manera equivalente a especificar *filename* es con el [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) opción del vinculador.

Código auxiliar es válido en un archivo de definición de módulo cuando se desea generar un VxD.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)