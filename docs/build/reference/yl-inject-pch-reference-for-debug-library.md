---
title: /Yl (Insertar referencia PCH para biblioteca de depuración)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 816ba66c94e616407a8891cd149a41e44e29358d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825722"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Insertar referencia PCH para biblioteca de depuración)

La opción **/YL** genera un símbolo único en un archivo de encabezado precompilado y se inserta una referencia a este símbolo en todos los archivos objeto que usan el encabezado precompilado.

## <a name="syntax"></a>Sintaxis

>**/YL**\
>**/YL**_Name_\
>**YL**

### <a name="arguments"></a>Argumentos

*name*<br/>
Nombre opcional que se usa como parte del símbolo único.

*\-*<br/>
Un guión (-) deshabilita explícitamente la opción del compilador **/YL** .

## <a name="remarks"></a>Observaciones

La opción del compilador **/YL** crea una definición de símbolo único en un archivo de encabezado precompilado creado con la opción [/YC](yc-create-precompiled-header-file.md) . Las referencias a este símbolo se insertan automáticamente en todos los archivos que incluyen el encabezado precompilado mediante la opción del compilador [/Yu](yu-use-precompiled-header-file.md) . La opción **/YL** está habilitada de forma predeterminada cuando se usa **/YC** para crear un archivo de encabezado precompilado.

La opción **/YL**_Name_ se usa para crear un símbolo identificable en el archivo de encabezado precompilado. El compilador usa el argumento *Name* como parte del nombre de símbolo representativo que `__@@_PchSym_@00@...@name`crea, similar a, donde los puntos suspensivos (...) representan una cadena de caracteres única generada por el compilador. Si se omite el argumento de *nombre* , el compilador genera automáticamente un nombre de símbolo. Normalmente, no es necesario conocer el nombre del símbolo. Sin embargo, cuando el proyecto usa más de un archivo de encabezado precompilado, la opción **/YL**_Name_ puede ser útil para determinar qué archivos de objeto usan el encabezado precompilado. Puede usar *Name* como una cadena de búsqueda para buscar la referencia de símbolos en un archivo de volcado de memoria.

**/YL-** deshabilita el comportamiento predeterminado y no coloca un símbolo de identificación en el archivo de encabezado precompilado. Los archivos compilados que incluyen este encabezado precompilado no obtienen una referencia de símbolo común.

Cuando no se especifica **/YC** , cualquier opción **/YL** no tiene ningún efecto, pero si se especifica, debe coincidir con cualquier opción **/YL** pasada cuando se especifica **/YC** .

Si usa las opciones **/YL-**, **/YC** y [/Z7](z7-zi-zi-debug-information-format.md) para compilar un archivo de encabezado precompilado, la información de depuración se almacena en el archivo objeto del archivo de código fuente utilizado para crear el encabezado precompilado, en lugar de un archivo. pdb independiente. Si este archivo objeto se convierte en parte de una biblioteca, pueden producirse errores [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) o advertencias de [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) en las compilaciones que usan esta biblioteca y el archivo de encabezado precompilado, si el archivo de código fuente utilizado para crear el archivo de encabezado precompilado no define ningún símbolo. El enlazador puede excluir el archivo objeto del vínculo, junto con la información de depuración asociada, cuando no se hace referencia a nada en el archivo objeto en el cliente de biblioteca. Para solucionar este problema, especifique **/YL** (o quite la opción **/YL-** ) cuando use **/YC** para crear el archivo de encabezado precompilado. Esto garantiza que el archivo objeto de la biblioteca que contiene la información de depuración se vincula en la compilación.

Para obtener más información sobre los encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](y-precompiled-headers.md)

- [Archivos de encabezado precompilados](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** de**C/C++** > de **propiedades** > de configuración.

1. Agregue la opción del compilador **/YL**_Name_ en el cuadro **opciones adicionales** . Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
