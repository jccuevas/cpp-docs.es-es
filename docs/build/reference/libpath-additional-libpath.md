---
title: /LIBPATH (Directorios de bibliotecas adicionales)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: ab586c788825a854e7d3cb3760da6e4e5558de3a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269220"
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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **General** página de propiedades.

1. Modificar el **directorios de bibliotecas adicionales** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
