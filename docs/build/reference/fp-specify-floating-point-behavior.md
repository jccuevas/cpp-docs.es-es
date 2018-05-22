---
title: -fp (Especificar comportamiento de punto flotante) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
dev_langs:
- C++
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 520a6e2d675c55e47a0424ab93c6a76d521f2358
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2018
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Especificar comportamiento de punto flotante)

Especifica el comportamiento de punto flotante en un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

> **/ fp:**[**precisa** | **excepto**[**-**] | **rápido** | **estricta**]

### <a name="arguments"></a>Argumentos

#### <a name="precise"></a>Precisa

El valor predeterminado de **/FP** es **/fp: precisa**.

El **/fp: precisa** marca mejora la coherencia de las pruebas de punto flotante de igualdad y desigualdad deshabilitando las optimizaciones que podrían cambiar la precisión de los cálculos de punto flotante. (Es necesario mantener una precisión específica para preservar la compatibilidad estricta con ANSI). De forma predeterminada, en el código para x86 arquitecturas que use x87 coprocesador las instrucciones, el compilador usa el coprocesador de 80 bits registros para almacenar los resultados intermedios de cálculos de punto flotante. Esto aumenta la velocidad del programa y reduce su tamaño. No obstante, dado que en el cálculo están involucrados tipos de datos de punto flotante que se representan en memoria con menos de 80 bits, utilizar los bits adicionales de precisión (80 bits menos el número de bits de un tipo de punto flotante más pequeño) en un cálculo laborioso puede generar resultados incoherentes.

Con **/fp: precisa** en x86 procesadores, el compilador realiza el redondeo en variables de tipo `float` a la precisión adecuada para asignaciones y conversiones de tipos y cuando se pasan parámetros a una función. Este redondeo garantiza que los datos no tengan un valor más significativo que la capacidad de su tipo. Un programa compilado con **/fp: precisa** puede ser más lento y mayor que otro compilado sin **/fp: precisa**. **/ fp: precisa** deshabilita los intrínsecos; la biblioteca en tiempo de ejecución estándar se utilizan en su lugar las rutinas. Para obtener más información, consulte [/Oi (Generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md).

El siguiente comportamiento de punto flotante se habilita con **/fp: precisa**:

- Contracciones: es decir, el uso de una operación compuesta que solo tiene un redondeo al final para reemplazar varias operaciones.

- Las optimizaciones de expresiones que no son válidas para valores especiales (NaN, +infinito, -infinito, +0, -0) no están permitidas. La optimizaciones x-x = > 0, x * 0 = > 0, x-0 = > x, x + 0 = > x y 0 x = > - x no son válidas por varias razones. (Vea IEEE 754 y el estándar C99).

- El compilador controla correctamente las comparaciones que implican NaN. Por ejemplo, x! = x se evalúa como **true** si `x` es NaN y las comparaciones ordenadas que implican NaN genera una excepción.

- La evaluación de la expresión se ajusta a C99 FLT_EVAL_METHOD=2, con la siguiente excepción: cuando se programa para procesadores x86, ya que la FPU se establece en una precisión de 53 bits, lo que se considera una precisión long-double.

- La multiplicación por 1,0 exactamente se transforma en un uso del otro factor. x * y\*1.0 se transforma en x\*y. De forma similar, x\*1.0\*y se transforma en x\*y.

- La división por 1,0 exactamente se transforma en un uso del dividendo. x * y/1.0 se transforma en x\*y. De forma similar, x / 1.0\*y se transforma en x\*y.

Usar **/fp: precisa** cuando [fenv_access](../../preprocessor/fenv-access.md) está activado deshabilita las optimizaciones, como evaluaciones de tiempo de compilación de expresiones de punto flotante. Por ejemplo, si usa [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) cambiar el modo de redondeo y el compilador realiza un cálculo de punto flotante, el modo de redondeo especificado no está en vigor a menos que `fenv_access`es ON.

**/ fp: precisa** reemplaza la **/Op** opción del compilador.

#### <a name="fast"></a>El rápido

El **/fp: Fast** opción crea el código más rápido en la mayoría de los casos por relaja las reglas para optimizar las operaciones de punto flotante. Esto permite al compilador optimizar el código de punto flotante para mejorar la velocidad en detrimento de la precisión y la exactitud. Cuando **/fp: Fast** se especifica, el compilador no puede redondeo correctamente en instrucciones de asignación, conversiones de tipo o llamadas de función y no puede realizar el redondeo de expresiones intermedias. El compilador puede reordenar las operaciones o realizar transformaciones algebraicas (por ejemplo, con arreglo a reglas asociativas y distributivas), sin que esto afecte a los resultados de precisión finita. El compilador puede cambiar las operaciones y los operandos a una precisión simple en lugar de seguir las reglas de promoción de tipos de C++. Siempre se habilitan las optimizaciones de contracción de específicos de punto flotante ([fp_contract](../../preprocessor/fp-contract.md) es ON). Excepciones de punto flotante y acceso de entorno FPU están deshabilitadas (**/fp: excepto-** está implícito y [fenv_access](../../preprocessor/fenv-access.md) es OFF).

**/ fp: Fast** no se puede usar con **/fp: strict** o **/fp: precisa**. Se utiliza la última opción especificada en la línea de comandos. Si se especifica **/fp: Fast** y **/fp: excepto** genera un error del compilador.

Especificar [/Za, /Ze (deshabilitar extensiones de lenguaje)](../../build/reference/za-ze-disable-language-extensions.md) (compatibilidad con ANSI) y **/fp: Fast** pueden provocar un comportamiento inesperado. Por ejemplo, las operaciones de punto flotante de precisión sencilla no se pueden redondear a precisión sencilla.

#### <a name="except"></a>Salvo

El **/fp: excepto** opción permite un modelo de excepción de punto flotante confiable. Las excepciones se generan inmediatamente después de desencadenarse. Esta opción está desactivada de forma predeterminada. Al anexar un signo menos a la opción (**/fp: excepto-**) deshabilita de forma explícita.

#### <a name="strict"></a>strict

El **/fp: strict** opción habilita el modelo de punto flotante más estricto. **/ fp: strict** hace [fp_contract](../../preprocessor/fp-contract.md) a establecerse en OFF y [fenv_access](../../preprocessor/fenv-access.md) para estar establecida en ON. **/ fp: excepto** está implícito y se puede deshabilitar mediante la especificación explícita **/fp: excepto-**. Cuando se usa con **/fp: excepto-**, **/fp: strict** exige la semántica estricta de punto flotante pero sin considerar eventos excepcionales.

## <a name="remarks"></a>Comentarios

Varios **/FP** opciones pueden especificarse en la misma compilación.

Para controlar el comportamiento de punto flotante por función, vea la [float_control](../../preprocessor/float-control.md) pragma. Esto invalida la **/FP** configuración del compilador. Como procedimiento de ingeniería aconsejable, se recomienda guardar y restaurar el comportamiento de punto flotante local:

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

La mayoría de las optimizaciones de punto flotante relacionadas con **/fp: strict**, **/fp: excepto** (y sus correspondientes directivas pragma) y el `fp_contract` pragma dependen del equipo. **/ fp: strict** y **/fp: excepto** no son compatibles con **/CLR**.

**/ fp: precisa** debería tratar la mayoría de los requisitos de punto flotante de una aplicación. Puede usar **/fp: excepto** y **/fp: strict**, pero puede haber cierto deterioro del rendimiento. Si el rendimiento es más importante, considere la posibilidad de usar **/fp: Fast**.

**/ fp: strict**, **/fp: Fast**, y **/fp: precisa** son modos de precisión (exactitud). Solo puede haber uno en vigor en un momento dado. Si ambos **/fp: strict** y **/fp: precisa** se especifican, el compilador utiliza el que procesa en último lugar. Ambos **/fp: strict** y **/fp: Fast** no se puede especificar.

Para obtener más información, consulte [Microsoft Visual C++ punto flotante optimización](floating-point-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración** > **C/C++** > **generación de código** página de propiedades.

1. Modificar el **modelo de punto flotante** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador](compiler-options.md)
- [Establecer las opciones del compilador](setting-compiler-options.md)
- [Microsoft Visual C++ flotante optimización de punto](floating-point-optimization.md)