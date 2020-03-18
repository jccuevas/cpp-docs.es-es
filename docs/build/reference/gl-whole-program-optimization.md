---
title: /GL (Optimización de todo el programa)
ms.date: 11/04/2016
f1_keywords:
- /gl
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 875865a32dcb80cb8a6d8fa53646260f3d9413a5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439657"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optimización de todo el programa)

Habilita la optimización completa del programa.

## <a name="syntax"></a>Sintaxis

```
/GL[-]
```

## <a name="remarks"></a>Observaciones

La optimización de todo el programa permite que el compilador realice optimizaciones con información sobre todos los módulos del programa. Sin la optimización de todo el programa, las optimizaciones se realizan en cada módulo (compilación).

La optimización de todo el programa está desactivada de forma predeterminada y debe habilitarse explícitamente. Sin embargo, también es posible deshabilitarlo explícitamente con **/GL-** .

Con información sobre todos los módulos, el compilador puede:

- Optimice el uso de registros a través de los límites de función.

- Realice un mejor trabajo de seguimiento de las modificaciones en los datos globales, lo que permite una reducción en el número de cargas y almacenes.

- Realice un mejor trabajo de seguimiento del conjunto de elementos posible modificado por una desreferenciación de puntero, lo que reduce el número de cargas y almacenes.

- Inserta una función en un módulo incluso cuando la función está definida en otro módulo.

los archivos. obj generados con **/GL** no estarán disponibles para estas utilidades del enlazador como [EDITBIN](editbin-reference.md) y [dumpbin](dumpbin-reference.md).

Si compila el programa con **/GL** y [/c](c-compile-without-linking.md), debe usar la opción del vinculador/LTCG para crear el archivo de salida.

[/Zi](z7-zi-zi-debug-information-format.md) no se puede usar con **/GL**

El formato de los archivos generados con **/GL** en la versión actual puede no ser legible en versiones posteriores C++de visual. No debe enviar un archivo. lib compuesto por archivos. obj que se generaron con **/GL** a menos que esté dispuesto a enviar copias del archivo. lib para todas las versiones de Visual C++ que espera que los usuarios usen, ahora y en el futuro.

los archivos. obj generados con los archivos de encabezado **/GL** y precompilado no deben usarse para compilar un archivo. lib a menos que el archivo. lib se vincule en el mismo equipo que generó el archivo **/GL** . obj. La información del archivo de encabezado precompilado del archivo. obj será necesaria en el momento de la vinculación.

Para obtener más información sobre las optimizaciones disponibles con y las limitaciones de la optimización de todo el programa, vea [/LTCG](ltcg-link-time-code-generation.md).  **/GL** también hace que la optimización guiada por perfiles esté disponible; Consulte/LTCG.  Al compilar para las optimizaciones guiadas por perfiles y si desea el orden de funciones de las optimizaciones guiadas por perfiles, debe compilar con [/GY](gy-enable-function-level-linking.md) o una opción del compilador que implique/GY.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Vea [/LTCG (generación de código en tiempo de vínculo)](ltcg-link-time-code-generation.md) para obtener información sobre cómo especificar **/GL** en el entorno de desarrollo.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
