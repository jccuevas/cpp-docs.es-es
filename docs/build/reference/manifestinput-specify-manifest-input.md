---
title: /MANIFESTINPUT (Especificar entrada de manifiestos)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606460"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Especificar entrada de manifiestos)

Especifica un archivo de entrada de manifiesto que se va a incluir en el manifiesto que está incrustado en la imagen.

## <a name="syntax"></a>Sintaxis

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>Parámetros

*filename*<br/>
El archivo de manifiesto que se va a incluir en el manifiesto incrustado.

## <a name="remarks"></a>Comentarios

La opción **/MANIFESTINPUT** especifica la ruta de acceso de un archivo de entrada que se va a usar para crear el manifiesto incrustado en una imagen ejecutable. Si tiene varios archivos de entrada de manifiesto, use el modificador varias veces, una vez para cada archivo de entrada. Los archivos de entrada de manifiesto se combinan para crear el manifiesto incrustado. Esta opción requiere la opción **/manifest: embed** .

Esta opción no se puede establecer directamente en Visual Studio. En su lugar, use la propiedad **archivos de manifiesto adicionales** del proyecto para especificar los archivos de manifiesto adicionales que se van a incluir. Para obtener más información, consulte [las páginas de propiedades de la herramienta manifiesto](manifest-tool-property-pages.md).

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
