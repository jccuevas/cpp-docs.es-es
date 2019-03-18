---
title: /DRIVER (Controlador de modo kernel de Windows NT)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: ab7253d7e386bf385bcb3a586c5e0e1c1e860694
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811685"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (Controlador de modo kernel de Windows NT)

>/ CONTROLADOR [: UPONLY |: WDM]

## <a name="remarks"></a>Comentarios

Use la **/DRIVER** opción del vinculador para compilar un controlador de modo kernel de Windows NT.

**UPONLY** hace que el vinculador agregue el **IMAGE_FILE_UP_SYSTEM_ONLY** a las características en el encabezado de salida para especificar que se trata de un controlador monoprocesador (UP). El sistema operativo se negará a cargar un controlador en un sistema multiprocesador (MP).

**/ Driver: WDM** hace que el vinculador establezca el **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** bit en el campo DllCharacteristics del encabezado opcional.

Si **/DRIVER** no se especifica, el vinculador no establece estos bits.

Si **/DRIVER** se especifica:

- **/ Fixed: no** está en vigor. Para obtener más información, consulte [/FIXED (Dirección base fija)](fixed-fixed-base-address.md).

- La extensión del archivo de salida se establece en .sys. Use **/OUT** para cambiar el nombre de archivo predeterminado y la extensión. Para obtener más información, consulte [/OUT (Nombre del archivo de salida)](out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modificar el **controlador** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Consulte [VCLinkerTool.driver propiedad](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
