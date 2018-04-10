---
title: -CONTROLADOR (controlador de modo Kernel de Windows NT) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs:
- C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29234e3c0e368c7710f9071c753422bc4e6ef2b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Controlador de modo kernel de Windows NT)

>/ CONTROLADOR [: UPONLY |: WDM]

## <a name="remarks"></a>Comentarios

Use la **Driver/Driver** opción del vinculador para crear un controlador de modo kernel de Windows NT.

**/DRIVER:UPONLY** hace que el vinculador agregar el **IMAGE_FILE_UP_SYSTEM_ONLY** bits para las características en el encabezado de salida para especificar que se trata de un controlador monoprocesador (UP). El sistema operativo no cargará un controlador MONOPROCESADOR en un sistema multiprocesador (MP).

**/ Driver: WDM** hace que el vinculador establecer el **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** de bits en el campo DllCharacteristics del encabezado opcional.

Si **Driver/Driver** no se especifica, el vinculador no establece estos bits.

Si **Driver/Driver** se especifica:

- **/ Fixed: no** está en vigor. Para obtener más información, consulte [/FIXED (Dirección base fija)](../../build/reference/fixed-fixed-base-address.md).

- La extensión del archivo de salida se establece en. sys. Use **/OUT** para cambiar el nombre de archivo predeterminado y la extensión. Para obtener más información, consulte [/OUT (Nombre del archivo de salida)](../../build/reference/out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **System** página de propiedades.

1. Modificar el **controlador** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea [VCLinkerTool.driver propiedad](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
[Opciones del vinculador](../../build/reference/linker-options.md)
