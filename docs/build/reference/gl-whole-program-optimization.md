---
title: /GL (Optimización de todo el programa)
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 7e9300c6c851eb013d8304bd90e3ca9aa4b2c022
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640833"
---
# <a name="gl-whole-program-optimization"></a>/GL (Optimización de todo el programa)

Habilita la optimización completa del programa.

## <a name="syntax"></a>Sintaxis

```
/GL[-]
```

## <a name="remarks"></a>Comentarios

Optimización de todo el programa permite que el compilador realice optimizaciones con información de todos los módulos en el programa. Sin la optimización de todo el programa, las optimizaciones se realizan en una por cada módulo (compilando).

Optimización de todo el programa está desactivada de forma predeterminada y debe habilitarse explícitamente. Sin embargo, también es posible deshabilitar explícitamente con **/GL-**.

Con información sobre todos los módulos, el compilador puede:

- Optimizar el uso de registros a través de límites de la función.

- Hacer mejor su trabajo de seguimiento de las modificaciones de datos globales, lo que permite una reducción en el número de cargas y almacenes.

- Hacer mejor su trabajo de seguimiento desreferenciar el posible conjunto de elementos modificados por un puntero, lo que reduce el número de cargas y almacenes.

- Inserte una función en un módulo, incluso cuando la función está definida en otro módulo.

archivos .obj generados con **/GL** no estará disponible para las utilidades del vinculador como [EDITBIN](../../build/reference/editbin-reference.md) y [DUMPBIN](../../build/reference/dumpbin-reference.md).

Si compila un programa con **/GL** y [/c](../../build/reference/c-compile-without-linking.md), debe usar la opción de vinculador/LTCG para crear el archivo de salida.

[/ Zi](../../build/reference/z7-zi-zi-debug-information-format.md) no se puede usar con   **/GL**

El formato de archivos generados con **/GL** en la versión actual puede no ser legible con versiones posteriores de Visual C++. No debe enviar un archivo .lib compuesto por archivos .obj que se hayan generado con **/GL** a menos que esté dispuesto a distribuir copias del archivo .lib para todas las versiones de Visual C++ esperan a los usuarios usar ahora y en el futuro.

archivos .obj generados con **/GL** y archivos de encabezado precompilados no deben usarse para crear un archivo .lib, a menos que se vinculará el archivo .lib en el mismo equipo que generó el **/GL** archivo .obj. Información del archivo de encabezado precompilado del archivo .obj se necesitará en tiempo de vinculación.

Para obtener más información sobre las optimizaciones disponibles con y las limitaciones de la optimización de todo el programa, consulte [/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **/ GL** también facilita la optimización guiada disponible perfiles; vea/LTCG.  Cuando se compila para guiada por perfiles optimizaciones y si desea que la función de ordenación de las optimizaciones guiadas por perfiles, debe compilar con [/Gy](../../build/reference/gy-enable-function-level-linking.md) o una opción del compilador que implique /Gy.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Consulte [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md) para obtener información sobre cómo especificar **/GL** en el entorno de desarrollo.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)