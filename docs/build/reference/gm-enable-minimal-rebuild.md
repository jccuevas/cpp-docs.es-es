---
title: /Gm (Habilitar recompilación mínima)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439646"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Habilitar recompilación mínima)

En desuso. Habilita la recompilación mínima, que determina si es necesario recompilar los archivos de origen de C++ que incluyen definiciones de clases de C++ cambiadas (almacenadas en archivos de encabezado (.h)).

## <a name="syntax"></a>Sintaxis

```
/Gm
```

## <a name="remarks"></a>Observaciones

**/GM** está en desuso. No puede desencadenar una compilación para determinados tipos de cambios en el archivo de encabezado. Puede quitar esta opción de forma segura de sus proyectos. Para mejorar los tiempos de compilación, se recomienda usar los encabezados precompilados y las opciones de compilación incremental y paralela en su lugar. Para obtener una lista de opciones del compilador en desuso, vea la sección Opciones del compilador en **desuso y quitadas** en [las opciones del compilador enumeradas por categoría](compiler-options-listed-by-category.md).

El compilador almacena la información de dependencias entre los archivos de origen y las definiciones de clases en el archivo .idb del proyecto durante la primera compilación. (La información de dependencias indica qué archivo de origen depende de qué definición de clase y en qué archivo .h está ubicada la definición). En las compilaciones sucesivas, se usa la información almacenada en el archivo .idb para determinar si es necesario compilar un archivo de origen, aunque incluya un archivo .h modificado.

> [!NOTE]
> La recompilación mínima se basa en las definiciones de clases que no cambian entre los archivos de inclusión. Las definiciones de clases deben ser globales del proyecto (solo debe haber una definición de cada clase), porque la información de dependencias del archivo .idb se crea para todo el proyecto. Si alguna clase del proyecto tiene más de una definición, deshabilite la recompilación mínima.

Dado que el vinculador incremental no admite los metadatos de Windows incluidos en los archivos. obj mediante la opción [/ZW (compilación Windows Runtime)](zw-windows-runtime-compilation.md) , la opción **/GM** no es compatible con **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > página de propiedades **generación de código** de **C/C++**  > .

1. Modifique la propiedad **Habilitar recompilación mínima** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
