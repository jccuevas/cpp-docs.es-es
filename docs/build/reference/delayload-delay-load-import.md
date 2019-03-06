---
title: /DELAYLOAD (Retrasar importación de carga)
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: aa8cc5a565b4af625a1ee85f67ca1c82e065486b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416285"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Retrasar importación de carga)

> **/ DELAYLOAD:**_dllname_

## <a name="parameters"></a>Parámetros

*dllname*<br/>
Nombre de un archivo DLL cuya carga se desea retrasar.

## <a name="remarks"></a>Comentarios

La opción /DELAYLOAD hace que el archivo DLL especificado por `dllname` se cargue solo en la primera llamada del programa a una función en ese archivo DLL. Para obtener más información, consulte [compatibilidad con vinculador para archivos DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md). Puede usar esta opción tantas veces como sea necesario para especificar todos los archivos DLL que desee. Debe utilizar Delayimp.lib cuando enlace el programa o puede implementar su propia función del asistente de retraso de carga.

El [/DELAY](../../build/reference/delay-delay-load-import-settings.md) opción especifica el enlace y carga las opciones para cada archivo DLL de carga retrasada.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. En el **vinculador** carpeta, seleccione el **entrada** página de propiedades.

1. Modificar el **archivos DLL de carga de retraso** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
