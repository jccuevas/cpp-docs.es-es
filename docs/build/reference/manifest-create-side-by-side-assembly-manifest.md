---
title: -MANIFEST (crear manifiesto del ensamblado en paralelo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
dev_langs:
- C++
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 468c41fe9cda752dd2727e6c9ec5d29781ef113d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710416"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Crear el manifiesto del ensamblado simultáneo)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>Comentarios

/MANIFEST especifica que el vinculador debe crear un archivo de manifiesto en paralelo. Para obtener más información acerca de los archivos de manifiesto, vea [Manifest Files Reference](/windows/desktop/SbsCs/manifest-files-reference).

El valor predeterminado es /MANIFEST.

La opción /MANIFEST:EMBED especifica que el vinculador debe incrustar el archivo de manifiesto en la imagen como recurso de tipo RT_MANIFEST. El parámetro `ID` opcional es el id. de recurso que se utilizará para el manifiesto. Utilice un valor de 1 para un archivo ejecutable. Utilice un valor de 2 en un archivo DLL para habilitarlo si desea especificar dependencias privadas. Si no se especifica el parámetro `ID`, el valor predeterminado es 2 si se establece la opción /DLL; de lo contrario, el valor predeterminado es 1.

A partir de Visual Studio 2008, los archivos de manifiesto para archivos ejecutables contienen una sección que especifica la información de Control de cuentas de usuario (UAC). Si especifica /MANIFEST pero especifica ninguno [/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ni [/DLL](../../build/reference/dll-build-a-dll.md), un fragmento del UAC predeterminado que tiene la configuración de nivel de UAC *asInvoker* se inserta en el manifiesto. Para obtener más información acerca de los niveles UAC, consulte [/MANIFESTUAC (insertar información de UAC en el manifiesto)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

Para cambiar el comportamiento predeterminado de UAC, realice una de las siguientes operaciones:

- Especifique la opción /MANIFESTUAC y establezca el nivel de UAC en el nivel deseado.

- O bien, especifique la opción /MANIFESTUAC:NO si no desea generar un fragmento de UAC en el manifiesto.

Si no especifica /MANIFEST pero especifica [/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) comentarios, se crea un archivo de manifiesto. No se creará un archivo de manifiesto si especifica /MANIFEST:NO.

Si especifica /MANIFEST, el nombre del archivo de manifiesto coincidirá con el nombre del archivo de salida, pero se agregará .manifest al nombre de archivo. Por ejemplo, si el nombre del archivo de salida es MiArchivo.exe, el nombre del archivo de manifiesto será MiArchivo.exe.manifest.  Si especifica/ManifestFile:*nombre*, el nombre del manifiesto es lo que se especifica en *nombre*.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **vinculador** nodo.

1. Seleccione el **archivo de manifiesto** página de propiedades.

1. Modificar el **Generar manifiesto** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)