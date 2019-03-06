---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: fd2e7c4a3bd9fa09b88f4c3caa9b7d5b73c1ad98
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412944"
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
