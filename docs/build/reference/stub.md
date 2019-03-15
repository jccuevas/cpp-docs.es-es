---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 5224fdaa2a03dc615c9e7e7bb7f7ba822a40807e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822124"
---
# <a name="stub"></a>STUB

Cuando se utiliza en un archivo de definición de módulo que genera un controlador de dispositivo virtual (VxD), le permite especificar un nombre de archivo que contiene una estructura IMAGE_DOS_HEADER (definida en WINNT. H) que se usará en el controlador de dispositivo virtual (VxD), en lugar del encabezado predeterminado.

```
STUB:filename
```

## <a name="remarks"></a>Comentarios

Una manera equivalente a especificar *filename* es con el [/STUB](stub-ms-dos-stub-file-name.md) opción del vinculador.

Código auxiliar es válido en un archivo de definición de módulo cuando se desea generar un VxD.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
