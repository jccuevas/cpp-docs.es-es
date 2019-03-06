---
title: /D (Definiciones de preprocesador)
ms.date: 11/04/2016
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
ms.openlocfilehash: 089f34f6daa606ed2869852a04ee76c6bda8fe25
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424683"
---
# <a name="d-preprocessor-definitions"></a>/D (Definiciones de preprocesador)

Define un símbolo de preprocesamiento para un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

```
/Dname[= | # [{string | number}] ]
```

## <a name="remarks"></a>Comentarios

Puede usar este símbolo junto con `#if` o `#ifdef` para compilar condicionalmente archivos de código fuente. La definición del símbolo se mantiene vigente hasta que se vuelve a definir en el código o se anula en el código mediante la directiva `#undef`.

**/D** tiene el mismo efecto que la `#define` la directiva al principio de un archivo de código fuente, salvo que **/D** quita las comillas en la línea de comandos y `#define` conserva.

De forma predeterminada, el valor asociado a un símbolo es 1. Por ejemplo, **/D** `name` es equivalente a **/D**`name`**= 1**. En el ejemplo al final de este artículo, la definición de **prueba** se muestra para imprimir `1`.

Compilación con **/D** `name` **=** hace que el símbolo no tienen ningún valor asociado. Aunque el símbolo aún se pueda utilizar para compilar código condicionalmente, no se evalúa como ningún valor. En el ejemplo, si se compila con **/DTEST =**, se produce un error. Este comportamiento es similar al uso de `#define` con o sin un valor.

Este comando define el símbolo DEBUG en TEST.c:

**PRUEBA DE /DDEBUG CL. C**

Este comando quita todas las apariciones de la palabra clave `__far` en TEST.c:

**CL /D__far=  TEST.C**

El **CL** variable de entorno no se puede establecer en una cadena que contiene el signo igual. Para usar **/D** junto con el **CL** entorno variable, debe especificar el signo de número en lugar del signo igual:

```
SET CL=/DTEST#0
```

Al definir un símbolo de preprocesamiento en el símbolo del sistema, tenga en cuenta las reglas de análisis del shell y del compilador. Por ejemplo, para definir un símbolo de preprocesamiento de signo de porcentaje (%) en el programa, especifique los caracteres de signo de dos por ciento (%) en el símbolo del sistema: Si especifica solo una, se genera un error de análisis.

```
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. En el panel izquierdo, seleccione **propiedades de configuración**, **C o C++**, **preprocesador**.

1. En el panel derecho, en la columna derecha de la **definiciones del preprocesador** propiedad, abra el menú desplegable y elija **editar**.

1. En el **definiciones del preprocesador** cuadro de diálogo, agregar (uno por línea), modificar o eliminar una o varias definiciones. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Ejemplo

```
// cpp_D_compiler_option.cpp
// compile with: /DTEST
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

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/U, /u (Anular la definición de símbolos)](../../build/reference/u-u-undefine-symbols.md)<br/>
[#undef (directiva) (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br/>
[#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
