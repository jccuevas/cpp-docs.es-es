---
title: /FUNCTIONPADMIN (crear una imagen) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /functionpadmin
dev_langs:
- C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0a5ecfcc336e198de0adcc2393f740072d70cae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)

Prepara una imagen para la aplicación de revisiones recientes.

## <a name="syntax"></a>Sintaxis

> **/FUNCTIONPADMIN**[**:**_espacio_]  

### <a name="arguments"></a>Argumentos

*space*<br/>
La cantidad de relleno que se agregará al principio de cada función en bytes. En x86 el valor predeterminado es 5 bytes de relleno y en x64 el valor predeterminado es 6 bytes. En otros destinos se debe proporcionar un valor.

## <a name="remarks"></a>Comentarios

En orden para que el vinculador generar una imagen a, los archivos .obj deben haberse compilados con [/hotpatch (crear una imagen)](../../build/reference/hotpatch-create-hotpatchable-image.md).

Cuando se compila y vincula una imagen con una sola invocación de cl.exe, **/hotpatch** implica **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba el **/FUNCTIONPADMIN** opción **opciones adicionales**. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
