---
title: /FUNCTIONPADMIN (crear una imagen) | Microsoft Docs
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
ms.openlocfilehash: 7a82611c453a96e9247e414d6adb777c07320482
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703994"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Crear una imagen a la que se puede aplicar una revisión reciente)

Prepara una imagen para aplicar una revisión activa.

## <a name="syntax"></a>Sintaxis

> **/FUNCTIONPADMIN**[**:**_espacio_]

### <a name="arguments"></a>Argumentos

*space*<br/>
La cantidad de relleno que se agregará al principio de cada función en bytes. En x86 el valor predeterminado es 5 bytes de relleno y en x64 el valor predeterminado es 6 bytes. En otros destinos, debe proporcionarse un valor.

## <a name="remarks"></a>Comentarios

En orden para el vinculador generar una imagen a, los archivos .obj deben haberse compilados con [/hotpatch (crear una imagen)](../../build/reference/hotpatch-create-hotpatchable-image.md).

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
