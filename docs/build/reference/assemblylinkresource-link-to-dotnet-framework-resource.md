---
title: /ASSEMBLYLINKRESOURCE (Vincular a recursos de .NET Framework)
ms.date: 11/04/2016
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
ms.openlocfilehash: fb707a2721ed40ee3ec37d01b2bbcfcc51f05c38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295167"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Vincular a recursos de .NET Framework)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
El archivo de recursos de .NET Framework con el que quiere crear un vínculo desde el ensamblado.

## <a name="remarks"></a>Comentarios

La opción /ASSEMBLYLINKRESOURCE crea un vínculo a un recurso de .NET Framework en el archivo de salida. el archivo de recursos no se coloca en el archivo de salida. [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) incrusta un archivo de recursos en el archivo de salida.

Recursos vinculados son públicos en el ensamblado cuando se crean con el vinculador.

/ASSEMBLYLINKRESOURCE requiere que el compilador incluya [/CLR](clr-common-language-runtime-compilation.md); [/LN](ln-create-msil-module.md) o [/NOASSEMBLY](noassembly-create-a-msil-module.md) no se permite con/ASSEMBLYLINKRESOURCE.

Si *filename* es un archivo de recursos de .NET Framework creado, por ejemplo, con [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) o en el entorno de desarrollo, puede obtenerse con los miembros de la **System.Resources** espacio de nombres. Para obtener más información, consulte [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager). Para todos los demás recursos, utilice el **GetManifestResource** \* métodos en el **System.Reflection.Assembly** clase para acceder al recurso en tiempo de ejecución.

*nombre de archivo* puede tener cualquier formato de archivo. Por ejemplo, desea realizar una DLL nativa forme parte del ensamblado, por lo que se puede instalar en la caché Global de ensamblados y accesible desde el código administrado del ensamblado.

Otras opciones del vinculador que afectan a la generación de ensamblado son:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
