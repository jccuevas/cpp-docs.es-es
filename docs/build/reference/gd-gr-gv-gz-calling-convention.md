---
title: / Gd, / gr, / GV, /Gz (convención de llamada) | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7e6c1466ecc7bce26eb4dabd816e1733f16ae13
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895141"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Convención de llamada)

Estas opciones determinan el orden en función de qué argumentos se insertan en la pila, si la función llamadora o la función llamada quita los argumentos de la pila al final de la llamada y la convención de decoración de nombres que utiliza el compilador para identificar funciones individuales.

## <a name="syntax"></a>Sintaxis

> **/Gd**<br/>
> **/Gr**<br/>
> **/Gv**<br/>
> **/GZ**<br/>

## <a name="remarks"></a>Comentarios

**/GD**, el valor predeterminado, especifica la [__cdecl](../../cpp/cdecl.md) convención de llamada para todas las funciones excepto el miembro de C++ funciones y las funciones marcadas [__stdcall](../../cpp/stdcall.md), [__ fastcall](../../cpp/fastcall.md), o [__vectorcall](../../cpp/vectorcall.md).

**/ GR** especifica la `__fastcall` convención de llamada para todas las funciones excepto las funciones miembro de C++, las funciones denominado `main`y las funciones marcadas `__cdecl`, `__stdcall`, o `__vectorcall`. Todos los `__fastcall` funciones deben tener prototipos. Esta convención de llamada solo está disponible en los compiladores destinados a x86 y se pasa por alto los compiladores que tienen como destino otras arquitecturas.

**/GZ** especifica la `__stdcall` convención de llamada para todas las funciones excepto las funciones miembro de C++, las funciones denominado `main`y las funciones marcadas `__cdecl`, `__fastcall`, o `__vectorcall`. Todos los `__stdcall` funciones deben tener prototipos. Esta convención de llamada solo está disponible en los compiladores destinados a x86 y se pasa por alto los compiladores que tienen como destino otras arquitecturas.

**GV** especifica la `__vectorcall` convención de llamada para todas las funciones excepto las funciones miembro de C++, las funciones llamadas main, las funciones con un `vararg` lista de argumentos variables o funciones que se marcan con un conflicto en `__cdecl`, `__stdcall`, o `__fastcall` atributo. Esta convención de llamada solo está disponible en las arquitecturas de x86 y x64 que admiten/arch: SSE2 y versiones posteriores y se pasa por alto los compiladores que tienen como destino la arquitectura ARM.

Las funciones que toman un número variable de argumentos deben marcarse `__cdecl`.

**/GD**, **/GR**, **GV** y **/Gz** no son compatibles con [/CLR: safe](../../build/reference/clr-common-language-runtime-compilation.md) o   **/CLR: pure**. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

> [!NOTE]
> De forma predeterminada para x86 procesadores, las funciones miembro de C++ utilizan [__thiscall](../../cpp/thiscall.md).

Para todos los procesadores, una función miembro que se marca explícitamente como `__cdecl`, `__fastcall`, `__vectorcall`, o `__stdcall` utiliza la convención de llamada especificada si no se omite en esa arquitectura. Una función miembro que toma un número variable de argumentos siempre usa el `__cdecl` convención de llamada.

Estas opciones del compilador no tienen ningún efecto en la decoración de nombres de funciones y métodos de C++. A menos que se declara como `extern "C"`, funciones y métodos de C++ usan un esquema de decoración de nombres diferente. Para obtener más información, consulte [nombres representativos](../../build/reference/decorated-names.md).

Para obtener más información sobre las convenciones de llamada, vea [convenciones de llamada](../../cpp/calling-conventions.md).

## <a name="cdecl-specifics"></a>específico de __cdecl

En x86 procesadores, todos los argumentos de función se pasan en la pila de derecha a izquierda. En ARM y x64 arquitecturas, algunos argumentos se pasan por registro y el resto se pasan en la pila de derecha a izquierda. La rutina de llamada extrae los argumentos de la pila.

Para C, la `__cdecl` usos de convención de nomenclatura del nombre de la función precedido por un carácter de subrayado ( `_` ); se realiza ninguna traducción de mayúsculas. A menos que se declara como `extern "C"`, las funciones de C++ usan un esquema de decoración de nombres diferente. Para obtener más información, consulte [nombres representativos](../../build/reference/decorated-names.md).

## <a name="fastcall-specifics"></a>específico de __fastcall

Parte de un `__fastcall` los argumentos de función se pasan en registros (para x86 procesadores, ECX y EDX), y el resto se insertan en la pila de derecha a izquierda. La rutina invocada obtiene estos argumentos de la pila antes de devolver. Por lo general, **/GR** reduce el tiempo de ejecución.

> [!NOTE]
> Tenga cuidado al usar el `__fastcall` convención de llamada para cualquier función que está escrito en lenguaje ensamblador en línea. El uso de registros podría entrar en conflicto con el uso del compilador.

Para C, la `__fastcall` usos de convención de nomenclatura del nombre de la función precedido por un signo de arroba (**\@**) seguido por el tamaño de los argumentos de función en bytes. No se realiza ninguna traducción de mayúsculas. El compilador usa esta plantilla para la convención de nomenclatura:

`@function_name@number`

Cuando se usa el `__fastcall` convención de nomenclatura, use los archivos de inclusión estándar. De lo contrario, obtendrá referencias externas sin resolver.

## <a name="stdcall-specifics"></a>específico de __stdcall

Un `__stdcall` los argumentos de función se insertan en la pila de derecha a izquierda y la función llamada obtiene estos argumentos de la pila antes de devolver.

Para C, la `__stdcall` usos de convención de nomenclatura del nombre de la función precedido por un carácter de subrayado (**\_**) y seguido por un signo de arroba (**\@**) y el tamaño de la función argumentos en bytes. No se lleva a cabo la traducción de mayúsculas y minúsculas. El compilador usa esta plantilla para la convención de nomenclatura:

`_functionname@number`

## <a name="vectorcall-specifics"></a>específicos de __vectorcall

Un `__vectorcall` argumentos de entero de la función se pasan por valor, utilizando hasta dos (en x86) o cuatro (en x64) entero registra y hasta seis registros de XMM se registra para punto flotante y valores del vector y el resto se pasan en la pila de derecha a izquierda. La función llamada limpia la pila antes de devolver. Vector y valores devueltos de punto flotante se devuelven en XMM0.

Para C, la `__vectorcall` convención de nomenclatura usa el nombre de función seguido por dos arrobas (**\@\@**) y el tamaño de los argumentos de función en bytes. No se lleva a cabo la traducción de mayúsculas y minúsculas. El compilador usa esta plantilla para la convención de nomenclatura:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **C o C++** > **avanzadas** página de propiedades.

1. Modificar el **la convención de llamada** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador](../../build/reference/compiler-options.md)
- [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
