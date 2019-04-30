---
title: /DEF (Especificar un archivo de definición de módulos)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: c08412fb50835485e7941b2bb1db088943387b71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272313"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Especificar un archivo de definición de módulos)

```
/DEF:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
El nombre de un archivo de definición de módulo (.def) que se pasarán al vinculador.

## <a name="remarks"></a>Comentarios

La opción /DEF pasa un archivo de definición de módulo (.def) al vinculador. Solo un archivo .def puede especificarse para el vínculo. Para obtener más información acerca de los archivos .def, vea [archivos de definición de módulo](module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **entrada** página de propiedades.

1. Modificar el **archivo de definición de módulo** propiedad.

Para especificar un archivo .def desde el entorno de desarrollo, debe agregarlo al proyecto junto con otros archivos y, a continuación, especifique el archivo a la opción/def.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
