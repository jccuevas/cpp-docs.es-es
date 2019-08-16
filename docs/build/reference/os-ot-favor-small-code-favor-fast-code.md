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
ms.openlocfilehash: 5bbdda07eacdb003515a40a93a232c0f8626ca89
ms.sourcegitcommit: aed09c9c05e6b031c8a9f87a8d6bbdaf253485e8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412244"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Favorecer código pequeño, favorecer código rápido)

Minimiza o maximiza el tamaño de los archivos exe y DLL.

## <a name="syntax"></a>Sintaxis

```
/Os
/Ot
```

## <a name="remarks"></a>Comentarios

**/OS** (favorecer código pequeño) reduce el tamaño de los archivos exe y DLL indicando al compilador que favorezca el tamaño frente a la velocidad. El compilador puede reducir muchas construcciones de C y C++ a secuencias funcionalmente similares de código máquina. En ocasiones, estas diferencias ofrecen contrapartidas de tamaño frente a velocidad. El **/Os** y **/Ot** opciones le permiten especificar una preferencia por una u otra:

**/Ot** (favorecer código rápido) maximiza la velocidad de los archivos exe y DLL indicando al compilador que favorezca la velocidad frente a tamaño. (Esto es el valor predeterminado). El compilador puede reducir muchas construcciones de C y C++ a secuencias funcionalmente similares de código máquina. En ocasiones, estas diferencias ofrecen contrapartidas de tamaño frente a velocidad. El **/Ot** opción está implícita en maximizar velocidad ([/O2](o1-o2-minimize-size-maximize-speed.md)) opción. El **/O2** opción combina varias opciones para generar un código muy rápido.

Si usas **/Os** o **/Ot**, a continuación, también debe especificar [/Og](og-global-optimizations.md) para optimizar el código.

> [!NOTE]
>  Información recopilada de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, [optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

**x86 específico**

Ejemplo de código siguiente muestra la diferencia entre el favorecer código pequeño ( **/Os**) Opciones y favorecer código rápido ( **/Ot**) opción:

> [!NOTE]
>  La siguiente describe el comportamiento esperado cuando se usa **/Os** o **/Ot**. Sin embargo, comportamiento del compilador puede producir entre versiones diferentes optimizaciones para el código siguiente.

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

Como se muestra en el fragmento de código máquina inferior, si DIFFER.c se compila para el tamaño ( **/Os**), el compilador implementa la expresión de multiplicación en la instrucción return explícitamente como una multiplicación para generar una secuencia de código breve pero más lenta:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Como alternativa, si DIFFER.c se compila para acelerar el proceso ( **/Ot**), el compilador implementa la expresión de multiplicación en la instrucción return como una serie de desplazamiento y `LEA` instrucciones para generar una secuencia rápida pero más larga de código:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**END x86 específico**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **optimización** página de propiedades.

1. Modificar el **tamaño o velocidad** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
