---
title: /Qsafe_fp_loads | Microsoft Docs
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e079e084c641318c9bec0820263487139b4d5076
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Requiere instrucciones de movimiento de enteros para los valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.

## <a name="syntax"></a>Sintaxis

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Comentarios

**/ Qsafe_fp_loads** solo está disponible en los compiladores que tienen como destino x86; no está disponible en los compiladores destinados a x64 o ARM.

**/ Qsafe_fp_loads** fuerza al compilador que utilice instrucciones de movimiento de enteros en lugar de instrucciones de movimiento de punto flotante para mover datos entre la memoria y MMX registros. Esta opción también deshabilita la optimización de la carga del Registro para los valores de punto flotante que se pueden cargar en varias rutas cuando el valor puede producir una excepción en la carga, por ejemplo, un valor NaN.

Esta opción se reemplaza por [/fp: excepto](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** especifica un subconjunto del comportamiento del compilador especificado por **/fp: excepto**.

**/ Qsafe_fp_loads** no es compatible con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) y [/fp: Fast](../../build/reference/fp-specify-floating-point-behavior.md). Para obtener más información acerca de las opciones de compilador de punto flotante, consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Escriba la opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
