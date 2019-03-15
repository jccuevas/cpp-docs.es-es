---
title: /Gm (Habilitar recompilación mínima)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808214"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Habilitar recompilación mínima)

Desusado. Habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C++ que incluyen definiciones de clases de C++ cambiadas (almacenadas en archivos de encabezado (.h)).

## <a name="syntax"></a>Sintaxis

```
/Gm
```

## <a name="remarks"></a>Comentarios

**/GM** está en desuso. No se puede desencadenar una compilación para determinados tipos de cambios de archivo de encabezado. Puede quitar esta opción en los proyectos. Para mejorar los tiempos de compilación, se recomienda utilizar encabezados precompilados y incremental y paralelo opciones de compilación en su lugar. Para obtener una lista de opciones del compilador en desuso, vea el **en desuso y opciones del compilador quitó** sección [Compiler Options Listed por categoría](compiler-options-listed-by-category.md).

El compilador almacena la información de dependencias entre los archivos de origen y las definiciones de clases en el archivo .idb del proyecto durante la primera compilación. (Información de dependencias indica qué archivo de origen depende de qué definición de clase, y qué archivo .h la definición se encuentra en). Las compilaciones posteriores utilizan la información almacenada en el archivo .idb para determinar si un archivo de origen debe compilarse, aunque incluya un archivo .h modificado.

> [!NOTE]
> La recompilación mínima se basa en las definiciones de clases que no cambian entre los archivos de inclusión. Las definiciones de clases deben ser globales del proyecto (solo debe haber una definición de cada clase), porque la información de dependencias del archivo .idb se crea para todo el proyecto. Si alguna clase del proyecto tiene más de una definición, deshabilite la recompilación mínima.

Dado que el enlazador incremental no admite los metadatos de Windows incluidos en los archivos .obj mediante la [/ZW (compilación de Windows en tiempo de ejecución)](zw-windows-runtime-compilation.md) opción, el **/Gm** es incompatible con la opción  **/ ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **generación de código** página de propiedades.

1. Modificar el **habilitar recompilación mínima** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
