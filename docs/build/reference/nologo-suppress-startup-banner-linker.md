---
title: /NOLOGO (Suprimir el titular de inicio) (Vinculador)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: 1b966c1f7af556a85aadcafaa8ed43da5b3f75df
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422161"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Suprimir el titular de inicio) (Vinculador)

```
/NOLOGO
```

## <a name="remarks"></a>Comentarios

La opción /NOLOGO impide ver el número de versión y mensaje de copyright.

Esta opción también suprime la repetición de archivos de comandos. Para obtener más información, consulte [archivos de comandos de vínculo](../../build/reference/link-command-files.md).

De forma predeterminada, esta información se envía mediante el enlazador para la ventana de salida. En la línea de comandos se envía a la salida estándar y puede redirigirse a un archivo.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Esta opción solo debe utilizarse desde la línea de comandos.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. No se puede cambiar esta opción del vinculador mediante programación.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
