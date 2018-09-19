---
title: -DEF (especificar archivo de definición de módulo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ec7458f5b81dd2b9d5aac49959b935f49377081
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720417"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Especificar un archivo de definición de módulos)

```
/DEF:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
El nombre de un archivo de definición de módulo (.def) que se pasarán al vinculador.

## <a name="remarks"></a>Comentarios

La opción /DEF pasa un archivo de definición de módulo (.def) al vinculador. Solo un archivo .def puede especificarse para el vínculo. Para obtener más información acerca de los archivos .def, vea [archivos de definición de módulo](../../build/reference/module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **entrada** página de propiedades.

1. Modificar el **archivo de definición de módulo** propiedad.

Para especificar un archivo .def desde el entorno de desarrollo, debe agregarlo al proyecto junto con otros archivos y, a continuación, especifique el archivo a la opción/def.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)