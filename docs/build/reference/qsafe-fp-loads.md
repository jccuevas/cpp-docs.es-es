---
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: 57aece79dfab617121371e0489aa80f18e143372
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57819699"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Requiere instrucciones de movimiento de enteros para los valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.

## <a name="syntax"></a>Sintaxis

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Comentarios

**/ Qsafe_fp_loads** solo está disponible en los compiladores que tienen como destino x86; no está disponible en los compiladores destinados a x64 o ARM.

**/ Qsafe_fp_loads** fuerza al compilador que use instrucciones de movimiento de enteros en lugar de instrucciones de movimiento de punto flotante para mover datos entre la memoria y MMX registra. Esta opción también deshabilita la optimización de la carga del Registro para los valores de punto flotante que se pueden cargar en varias rutas cuando el valor puede producir una excepción en la carga, por ejemplo, un valor NaN.

Esta opción se reemplaza por [/fp: excepto](fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** especifica un subconjunto del comportamiento del compilador especificado por **/fp: excepto**.

**/ Qsafe_fp_loads** no es compatible con [/CLR](clr-common-language-runtime-compilation.md) y [/fp: Fast](fp-specify-floating-point-behavior.md). Para obtener más información acerca de las opciones del compilador de punto flotante, vea [/fp (Especificar comportamiento de punto flotante)](fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Especifique la opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
