---
title: /constexpr (controlar la evaluación constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 178acc548fb9c89dcfde104d2a12d85637440e28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294257"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (controlar la evaluación constexpr)

Use la **/constexpr** opciones del compilador para los parámetros de control para **constexpr** evaluación en tiempo de compilación.

## <a name="syntax"></a>Sintaxis

> **/constexpr:depth**<em>N</em>
>  **/constexpr:backtrace**<em>N</em>
>  **/constexpr:steps**<em>N</em>

## <a name="arguments"></a>Argumentos

**profundidad**<em>N</em> limitar la profundidad de recursiva **constexpr** invocación de función *N* niveles. El valor predeterminado es 512.

**seguimiento regresivo**<em>N</em> mostrar hasta *N* **constexpr** evaluaciones en diagnósticos. El valor predeterminado es 10.

**pasos**<em>N</em> Terminate **constexpr** evaluación después *N* pasos. El valor predeterminado es 100.000.

## <a name="remarks"></a>Comentarios

El **/constexpr** opciones del compilador de controlan la evaluación de tiempo de compilación de **constexpr** expresiones. Pasos para la evaluación, los niveles de recursividad y seguimiento regresivo profundidad se controlan para evitar que el compilador dedicar demasiado tiempo en **constexpr** evaluación. Para obtener más información sobre la **constexpr** elemento del lenguaje, consulte [constexpr (C++)](../../cpp/constexpr-cpp.md).

El **/constexpr** opciones están disponibles a partir de Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

2. En **propiedades de configuración**, expanda el **C o C++** carpeta y elija el **línea de comandos** página de propiedades.

3. Escriba cualquier **/constexpr** opciones del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
