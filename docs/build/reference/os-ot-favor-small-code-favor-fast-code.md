---
title: /Os, /Ot (Favorecer código pequeño, favorecer código rápido)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336187"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Favorecer código pequeño, favorecer código rápido)

Minimiza o maximiza el tamaño de los ARCHIVOS EXE y DLL.

## <a name="syntax"></a>Sintaxis

```
/Os
/Ot
```

## <a name="remarks"></a>Observaciones

**/Os** (Favor Small Code) minimiza el tamaño de los ARCHIVOS USB y DLL indicando al compilador que favorezca el tamaño sobre la velocidad. El compilador puede reducir muchas construcciones C y C++ a secuencias funcionalmente similares de código de máquina. Ocasionalmente, estas diferencias ofrecen compensaciones de tamaño frente a velocidad. Las opciones **/Os** y **/Ot** le permiten especificar una preferencia para una sobre la otra:

**/Ot** (Favor Fast Code) maximiza la velocidad de los ARCHIVOS USB y DLL indicando al compilador que favorezca la velocidad sobre el tamaño. (Este es el valor predeterminado.) El compilador puede reducir muchas construcciones C y C++ a secuencias funcionalmente similares de código de máquina. Ocasionalmente, estas diferencias ofrecen compensaciones de tamaño frente a velocidad. La opción **/Ot** está implícita en la opción Maximizar velocidad ([/O2](o1-o2-minimize-size-maximize-speed.md)). La opción **/O2** combina varias opciones para producir código muy rápido.

Si utiliza **/Os** o **/Ot**, también debe especificar [/Og](og-global-optimizations.md) para optimizar el código.

> [!NOTE]
> La información recopilada de las ejecuciones de prueba de generación de perfiles invalidará las optimizaciones que, de lo contrario, estarían en vigor si especifica **/Ob**, **/Os**o **/Ot**. Para obtener más información, [Optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

**Específico de x86**

El siguiente código de ejemplo muestra la diferencia entre las opciones Favorecer código pequeño (**/Os**) y la opción Favorecer código rápido (**/Ot**):

> [!NOTE]
> A continuación se describe el comportamiento esperado al utilizar **/Os** o **/Ot**. Sin embargo, el comportamiento del compilador de una versión a otra puede dar lugar a diferentes optimizaciones para el código siguiente.

```
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

Como se muestra en el fragmento de código de máquina siguiente, cuando DIFFER.c se compila para el tamaño (**/Os**), el compilador implementa la expresión de multiplicación en la instrucción return explícitamente como una multiplicación para producir una secuencia corta pero más lenta de código:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Como alternativa, cuando DIFFER.c se compila para speed (**/Ot**), el compilador implementa la `LEA` expresión multiply en la instrucción return como una serie de shift e instrucciones para producir una secuencia rápida pero más larga de código:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**FIN x86 Específico**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Optimización.**

1. Modifique la propiedad **Tamaño de favor o Velocidad.**

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Consulte también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
