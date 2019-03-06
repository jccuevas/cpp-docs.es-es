---
title: /MANIFESTINPUT (Especificar entrada de manifiestos)
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: f0b60b1f9ebff4547017fcfac586f00625311937
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418817"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Especificar entrada de manifiestos)

Especifica un archivo de entrada de manifiesto debe incluir en el manifiesto que se incrusta en la imagen.

## <a name="syntax"></a>Sintaxis

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
El archivo de manifiesto debe incluir en el manifiesto incrustado.

## <a name="remarks"></a>Comentarios

El **/MANIFESTINPUT** opción especifica la ruta de acceso de archivo de entrada se usa para crear el manifiesto incrustado en una imagen ejecutable. Si tiene un manifiesto varios archivos de entrada, utilice el modificador varias veces: una vez para cada archivo de entrada. Los archivos de entrada de manifiesto se combinan para crear el manifiesto incrustado. Esta opción requiere el **/MANIFEST: EMBED** opción.

Esta opción no se puede establecer directamente en Visual Studio. En su lugar, use el **archivos de manifiesto adicionales** propiedad del proyecto para especificar los archivos de manifiesto adicionales para incluir. Para obtener más información, consulte [entrada y salida, herramienta manifiesto, propiedades de configuración, \<NombreDelProyecto > cuadro de diálogo páginas de propiedades](../../ide/input-and-output-manifest-tool.md).

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
