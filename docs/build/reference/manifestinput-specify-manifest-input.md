---
title: /MANIFESTINPUT (Especificar entrada de manifiestos)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337508"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Especificar entrada de manifiestos)

Especifica un archivo de entrada de manifiesto que se incluirá en el manifiesto incrustado en la imagen.

## <a name="syntax"></a>Sintaxis

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parámetros

*Nombre*<br/>
El archivo de manifiesto que se incluirá en el manifiesto incrustado.

## <a name="remarks"></a>Observaciones

La opción **/MANIFESTINPUT** especifica la ruta de acceso de un archivo de entrada que se usará para crear el manifiesto incrustado en una imagen ejecutable. Si tiene varios archivos de entrada de manifiesto, utilice el modificador varias veces, una vez para cada archivo de entrada. Los archivos de entrada de manifiesto se combinan para crear el manifiesto incrustado. Esta opción requiere la opción **/MANIFEST:EMBED.**

Esta opción no se puede establecer directamente en Visual Studio. En su lugar, use la propiedad Archivos de **manifiesto adicionales** del proyecto para especificar archivos de manifiesto adicionales que se incluirán. Para obtener más información, vea [Páginas](manifest-tool-property-pages.md)de propiedades de herramientas de manifiesto .

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones de MSVC Linker](linker-options.md)
