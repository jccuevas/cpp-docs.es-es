---
title: /ASSEMBLYDEBUG (Agregar DebuggableAttribute)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: 7e0a2133549a72fa747c67b40f9de1f8f48362b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426542"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (Agregar DebuggableAttribute)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ASSEMBLYDEBUG emite el **DebuggableAttribute** atributo con depuración información seguimiento y deshabilita las optimizaciones JIT. Esto es lo mismo que especificar el siguiente atributo de origen:

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

/ ASSEMBLYDEBUG: DISABLE emite el **DebuggableAttribute** atributo pero deshabilita el seguimiento de información de depuración y habilita las optimizaciones JIT. Esto es lo mismo que especificar el siguiente atributo de origen:

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

El valor predeterminado es no emitir el **DebuggableAttribute** atributo.

DebuggableAttribute también puede agregarse a un ensamblado directamente en el código fuente. Por ejemplo,

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>Comentarios

Es necesario especificar explícitamente que una imagen administrada sea depurable. Uso de [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) por sí solo no es suficiente.

Otras opciones del vinculador que afectan a la generación de ensamblado son:

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depurar** página de propiedades.

1. Modificar el **ensamblado depurable** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
