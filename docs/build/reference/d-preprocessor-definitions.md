---
title: /D (Definiciones de preprocesador)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: b10d611d38508f5696dd3b72fb8458e9b61082c8
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230395"
---
# <a name="d-preprocessor-definitions"></a>/D (Definiciones de preprocesador)

Define un símbolo de preprocesamiento para un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

> **/D** ]nombre | [`=`[{ *número* decadena}]] | \`#` \[
> **/D** \[ ]nombre [[{`=` número decadena | }]] |  `"``#``"`

## <a name="remarks"></a>Comentarios

Puede usar este símbolo junto con `#if` o `#ifdef` para compilar condicionalmente archivos de código fuente. La definición del símbolo permanece en vigor hasta que se redefine en el código o no está definida en el código mediante una `#undef` Directiva.

**/D** tiene el mismo efecto que una `#define` Directiva al principio de un archivo de código fuente. La diferencia es que **/d** quita las comillas en la línea de comandos y `#define` una directiva las mantiene. Puede tener un espacio en blanco entre **/d** y el símbolo. No puede haber un espacio en blanco entre el símbolo y el signo igual, o entre el signo igual y cualquier valor asignado.

De forma predeterminada, el valor asociado a un símbolo es 1. Por ejemplo, `/D name` es equivalente a `/D name=1`. En el ejemplo al final de este artículo, se muestra la definición `TEST` de para imprimir. `1`

La compilación mediante hacequeelnombredelsímbolonotenganingúnvalor`/D name=` asociado. Aunque el símbolo aún se pueda utilizar para compilar código condicionalmente, no se evalúa como ningún valor. En el ejemplo, si realiza la compilación con `/DTEST=`, se produce un error. Este comportamiento es similar al uso de `#define` con o sin un valor.

La opción **/d** no admite definiciones de macros similares a funciones. Para insertar definiciones que no se pueden definir en la línea de comandos, considere la opción del compilador [/Fi (asignar nombre al archivo de inclusión obligatorio)](fi-name-forced-include-file.md) .

Puede usar **/d** varias veces en la línea de comandos para definir símbolos adicionales. Si el mismo símbolo se define más de una vez, se usa la última definición.

Este comando define el símbolo DEBUG en TEST.c:

```cmd
CL /DDEBUG TEST.C
```

Este comando quita todas las apariciones de la palabra clave `__far` en TEST.c:

```cmd
CL /D __far= TEST.C
```

La variable de entorno de **cl** no se puede establecer en una cadena que contenga el signo igual. Para usar **/d** junto con la variable de entorno de **cl** , debe especificar el signo de`#`número () en lugar del signo igual:

```cmd
SET CL=/DTEST#0
```

Al definir un símbolo de preprocesamiento en el símbolo del sistema, tenga en cuenta las reglas de análisis del shell y del compilador. Por ejemplo, para definir un símbolo de preprocesamiento de signo de porcentaje`%`() en el programa, especifique dos caracteres de signo de`%%`porcentaje () en el símbolo del sistema. Si solo especifica uno, se emite un error de análisis.

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. En el panel izquierdo, seleccione **propiedades de configuración**, **CC++/** , **preprocesador**.

1. En el panel derecho, en la columna derecha de la propiedad **definiciones de preprocesador** , abra el menú desplegable y elija **Editar**.

1. En el cuadro de diálogo **definiciones de preprocesador** , agregue (uno por línea), modifique o elimine una o más definiciones. Elija **Aceptar** para guardar los cambios.

   No es necesario incluir el prefijo de opción '/D ' en las definiciones que especifique aquí. En la página de propiedades, las definiciones se separan mediante`;`signos de punto y coma ().

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Ejemplo

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)\
[/FI (asignar nombre al archivo de inclusión obligatorio)](fi-name-forced-include-file.md)\
[/U,/u (anular la definición de símbolos)](u-u-undefine-symbols.md)\
[#undef (directiva) (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
