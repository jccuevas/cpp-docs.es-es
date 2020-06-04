---
title: /ASSEMBLYMODULE (Agregar un módulo MSIL al ensamblado)
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: 728e8a84ff8d1afac99f99dbb975c7fd9360bcc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273025"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (Agregar un módulo MSIL al ensamblado)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
El módulo que van a incluir en este ensamblado.

## <a name="remarks"></a>Comentarios

La opción /ASSEMBLYMODULE permite agregar una referencia de módulo a un ensamblado. Información de tipo en el módulo no estará disponible para el programa de ensamblado que agregó la referencia de módulo. Sin embargo, la información de tipo en el módulo estará disponible para cualquier programa que hace referencia al ensamblado.

Use [#using](../../preprocessor/hash-using-directive-cpp.md) para agregar una referencia de módulo a un ensamblado y disponer de información de tipo del módulo del programa de ensamblado.

Por ejemplo, considere el siguiente escenario:

1. Crear un módulo con [/LN](ln-create-msil-module.md).

1. Use /ASSEMBLYMODULE en otro proyecto para incluir el módulo en la compilación actual, lo cual creará un ensamblado. Este proyecto no hará referencia al módulo con `#using`.

1. Cualquier proyecto que hace referencia a este ensamblado ahora también puede usar los tipos del módulo.

Otras opciones del vinculador que afectan a la generación de ensamblado son:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

El vinculador MSVC acepta archivos .netmodule como entrada y el archivo de salida generado por el vinculador será un ensamblado o .netmodule sin ninguna dependencia de tiempo de ejecución en cualquiera de los archivos .netmodule que se utilizaron como entrada del vinculador.  Para más información, consulte [Archivos .netmodule como entrada del vinculador](netmodule-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **entrada** página de propiedades.

1. Modificar el **Agregar módulo al ensamblado** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
