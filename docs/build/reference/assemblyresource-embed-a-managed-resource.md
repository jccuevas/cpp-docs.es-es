---
title: /ASSEMBLYRESOURCE (Incrustar un recurso administrado)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: 566a667ababaa67c7aff71861b111416abbbd878
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486612"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Incrustar un recurso administrado)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Parámetros

*filename*<br/>
El recurso administrado que desea insertar en este ensamblado.

*name*<br/>
Opcional. El nombre lógico del recurso; el nombre utilizado para cargar el recurso. El valor predeterminado es el nombre del archivo.

Si lo desea, puede especificar si el archivo debe ser privado en el manifiesto del ensamblado. De forma predeterminada, *nombre* es público en el ensamblado.

## <a name="remarks"></a>Comentarios

Utilice la opción/ASSEMBLYRESOURCE para incrustar un recurso en un ensamblado.

Los recursos son públicos en el ensamblado cuando se crean con el vinculador. El vinculador no permite cambiar el nombre del recurso en el ensamblado.

Si *filename* es un archivo de recursos (.resources) de .NET Framework creado, por ejemplo, con el [generador de archivos de recursos (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) o en el entorno de desarrollo, puede obtenerse con los miembros de la **System.Resources** espacio de nombres (consulte [System.Resources.ResourceManager](https://msdn.microsoft.com/library/system.resources.resourcemanager.aspx) para obtener más información). Para todos los demás recursos, utilice el **GetManifestResource** \* métodos en **System.Reflection.Assembly** clase para acceder al recurso en tiempo de ejecución.

Otras opciones del vinculador que afectan a la generación de ensamblado son:

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **entrada** página de propiedades.

1. Modificar el **incrustar un archivo de recursos administrado** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)