---
title: -LIBPATH (directorios de bibliotecas adicionales) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 784281df23b0a8d43625766297b6cbbd20179c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717202"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (Directorios de bibliotecas adicionales)

```
/LIBPATH:dir
```

## <a name="parameters"></a>Parámetros

*dir*<br/>
Especifica una ruta de acceso que el enlazador buscará antes de que busca en la ruta de acceso especificada en la opción de entorno LIB.

## <a name="remarks"></a>Comentarios

Utilice la opción/libpath para invalidar la ruta de acceso de la biblioteca de entorno. El enlazador buscará primero en la ruta de acceso especificada por esta opción y, a continuación, buscar en la ruta de acceso especificada en la variable de entorno LIB. Puede especificar un único directorio para cada opción /LIBPATH que especifique. Si desea especificar más de un directorio, debe especificar varias opciones/LIBPATH. El enlazador buscará los directorios especificados en orden.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **General** página de propiedades.

1. Modificar el **directorios de bibliotecas adicionales** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)