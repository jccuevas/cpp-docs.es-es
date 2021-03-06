---
title: /Gd, /Gr, /Gv, /Gz (Convención de llamada)
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: 73fce079a98a3f4afaa35f8b8c6630fc8a9b4ca4
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825531"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Convención de llamada)

Estas opciones determinan el orden en el que se insertan los argumentos de función en la pila, si la función de llamador o de llamada quita los argumentos de la pila al final de la llamada y la convención de decoración de nombres que el compilador usa para identificar funciones individuales.

## <a name="syntax"></a>Sintaxis

> **/GD**\
> **/Gr**\
> **/GV**\
> **/GZ**

## <a name="remarks"></a>Observaciones

**/Gd**, la configuración predeterminada, especifica la convención de llamada [__cdecl](../../cpp/cdecl.md) para todas las funciones excepto las funciones miembro de C++ y las funciones que se marcan como [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md) o [__vectorcall](../../cpp/vectorcall.md).

**/Gr** especifica la `__fastcall` Convención de llamada para todas las funciones excepto las funciones miembro de `main`C++, las funciones denominadas `__cdecl`y `__stdcall`las funciones `__vectorcall`marcadas como, o. Todas las funciones `__fastcall` deben tener prototipos. Esta convención de llamada solo está disponible en los compiladores destinados a x86 y la pasan por alto los compiladores que tienen como destino otras arquitecturas.

**/Gz** especifica la `__stdcall` Convención de llamada para todas las funciones excepto las funciones miembro de `main`C++, las funciones denominadas `__cdecl`y `__fastcall`las funciones `__vectorcall`marcadas como, o. Todas las funciones `__stdcall` deben tener prototipos. Esta convención de llamada solo está disponible en los compiladores destinados a x86 y la pasan por alto los compiladores que tienen como destino otras arquitecturas.

**/GV** especifica la `__vectorcall` Convención de llamada para todas las funciones excepto las funciones miembro de `main`C++, las funciones `vararg` denominadas, las funciones con una lista de argumentos de variable o `__cdecl`las `__stdcall`funciones marcadas con un atributo, o `__fastcall` en conflicto. Esta convención de llamada solo está disponible en las arquitecturas de x86 y x64 que admiten /arch:SSE2 y versiones posteriores, y la pasan por alto los compiladores que tienen como destino la arquitectura ARM.

Las funciones que toman un número variable de argumentos deben marcarse con `__cdecl`.

**/Gd**, **/Gr**, **/Gv** y **/Gz** no son compatibles con [/clr:safe](clr-common-language-runtime-compilation.md) o **/clr:pure**. Las opciones del compilador **/clr:pure** y **/clr:safe** han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores.

> [!NOTE]
> De forma predeterminada para los procesadores x86, las funciones miembro de C++ usan [__thiscall](../../cpp/thiscall.md).

Para todos los procesadores, una función miembro que se marca explícitamente como `__cdecl`, `__fastcall`, `__vectorcall` o `__stdcall` usa la convención de llamada especificada si no se omite en esa arquitectura. Una función miembro que toma un número variable de argumentos siempre usa la convención de llamada `__cdecl`.

Estas opciones del compilador no tienen ningún efecto en la decoración de nombre de los métodos y las funciones de C++. A menos que se declare como `extern "C"`, los métodos y las funciones de C++ usan un esquema de decoración de nombres diferente. Para más información, vea [Nombres decorados](decorated-names.md).

Si quiere saber más sobre las convenciones de llamada, vea [Convenciones de llamada](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>Especificaciones de __cdecl

En los procesadores x86, todos los argumentos de función se pasan a la pila de derecha a izquierda. En las arquitecturas de ARM y x64, algunos argumentos los pasa el registro y el resto se pasan a la pila de derecha a izquierda. La rutina de llamada extraen los argumentos de la pila.

Para C, la convención de nomenclatura `__cdecl` usa el nombre de función precedido por un carácter de subrayado (`_`); no se realiza ninguna conversión de mayúsculas. A menos que se declaren como `extern "C"`, las funciones de C++ usan un esquema de decoración de nombres diferente. Para más información, vea [Nombres decorados](decorated-names.md).

## <a name="__fastcall-specifics"></a>Especificaciones de __fastcall

Parte de los argumentos de una función `__fastcall` se pasan en registros (para procesadores x86, ECX y EDX), y el resto se insertan en la pila de derecha a izquierda. La rutina de llamada extrae estos argumentos de la pila antes de devolver resultados. Por lo general, **/Gr** reduce el tiempo de ejecución.

> [!NOTE]
> Tenga cuidado al usar la convención de llamada `__fastcall` para cualquier función que esté escrita en lenguaje ensamblador alineado. El uso de registros podría entrar en conflicto con el uso del compilador.

En el caso de `__fastcall` C, la Convención de nomenclatura utiliza el nombre de la función precedido por un signo de arroba (**\@**) seguido del tamaño de los argumentos de la función en bytes. No se realiza ninguna conversión de mayúsculas y minúsculas. El compilador usa esta plantilla para la convención de nomenclatura:

`@function_name@number`

Cuando use la convención de nomenclatura `__fastcall`, use los archivos de inclusión estándar. En caso contrario, obtendrá referencias externas sin resolver.

## <a name="__stdcall-specifics"></a>Especificaciones de __stdcall

Los argumentos de la función `__stdcall` se insertan en la pila de derecha a izquierda y la función a la que se ha llamado extrae estos argumentos de la pila antes de devolver resultados.

En el caso de `__stdcall` C, la Convención de nomenclatura utiliza el nombre de función precedido**\_** por un carácter de subrayado (**\@**) y seguido de un signo de arroba () y el tamaño de los argumentos de la función en bytes. No se lleva a cabo la traducción de mayúsculas y minúsculas. El compilador usa esta plantilla para la convención de nomenclatura:

`_functionname@number`

## <a name="__vectorcall-specifics"></a>Especificaciones de __vectorcall

Los `__vectorcall` argumentos de entero de una función se pasan por valor, usando hasta dos registros de tipo entero (en x86) o cuatro (en x64), y hasta seis registros de XMM para los valores de punto flotante y Vector, y el resto se pasan en la pila de derecha a izquierda. La función a la que se ha llamado limpia la pila antes de devolver resultados. Los valores devueltos del vector y el punto flotante se devuelven en XMM0.

En el caso de `__vectorcall` C, la Convención de nomenclatura utiliza el nombre de la función**\@** seguido de dos símbolos de arroba () y el tamaño de los argumentos de la función en bytes. No se lleva a cabo la traducción de mayúsculas y minúsculas. El compilador usa esta plantilla para la convención de nomenclatura:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**avanzadas** de **C/C++** > .

1. Modifique la propiedad **Convención de llamada**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Consulte también

- [Opciones del compilador de MSVC](compiler-options.md)
- [Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
