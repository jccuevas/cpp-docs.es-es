---
title: /KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
ms.openlocfilehash: 96d2f5fed0e450224f82ee909cea9d56082505fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291618"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>Argumentos

*name*<br/>
Contenedor que contiene la clave. Escriba la cadena entre comillas dobles ("") si contiene un espacio.

## <a name="remarks"></a>Comentarios

El vinculador crea un ensamblado firmado insertando una clave pública en el manifiesto del ensamblado y firma el ensamblado final con la clave privada. Para generar un archivo de clave, escriba [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* en la línea de comandos. **sn -i** instala el par de claves en un contenedor.

Si se compila con [/LN](ln-create-msil-module.md), el nombre del archivo de clave se mantiene en el módulo y se incorpora al ensamblado que se crea cuando se compila un ensamblado que incluye una referencia explícita al módulo, a través de [#using](../../preprocessor/hash-using-directive-cpp.md), o al vincular con [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md).

También puede pasar la información de cifrado al compilador con [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Use [/DELAYSIGN](delaysign-partially-sign-an-assembly.md) si desea firmar parcialmente un ensamblado. Consulte [ensamblados de nombre seguro (firma de ensamblados) (C++ / c++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) para obtener más información sobre cómo firmar un ensamblado.

Otras opciones del vinculador que afectan a la generación de ensamblado son:

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

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
