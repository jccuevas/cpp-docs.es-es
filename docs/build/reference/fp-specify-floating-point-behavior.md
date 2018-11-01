---
title: /fp (Especificar comportamiento de punto flotante)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: 8b948edba3244eb22089b2ef5b4c8131736e1fb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452577"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Especificar comportamiento de punto flotante)

Especifica el comportamiento de punto flotante en un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

> **/ fp:**[**precisa** | **excepto**[**-**] | **rápido** | **strict**]

### <a name="arguments"></a>Argumentos

#### <a name="precise"></a>Precisa

El valor predeterminado de **/FP** es **/fp: precisa**.

El **/fp: precisa** marca mejora la coherencia de las pruebas de punto flotante de igualdad y desigualdad, deshabilitando las optimizaciones que pudieran cambiar la precisión de los cálculos de punto flotante. (Es necesario mantener una precisión específica para preservar la compatibilidad estricta con ANSI). De forma predeterminada, en el código para x86 arquitecturas que use x87 coprocesador las instrucciones, el compilador usa el coprocesador de 80 bits registros para almacenar los resultados intermedios de cálculos de punto flotante. Esto aumenta la velocidad del programa y reduce su tamaño. No obstante, dado que en el cálculo están involucrados tipos de datos de punto flotante que se representan en memoria con menos de 80 bits, utilizar los bits adicionales de precisión (80 bits menos el número de bits de un tipo de punto flotante más pequeño) en un cálculo laborioso puede generar resultados incoherentes.

Con **/fp: precisa** en x86 procesadores, el compilador realiza el redondeo en las variables de tipo `float` a la precisión adecuada para asignaciones y conversiones de tipos y cuando se pasan parámetros a una función. Este redondeo garantiza que los datos no tengan un valor más significativo que la capacidad de su tipo. Un programa compilado con **/fp: precisa** puede ser más lento y mayor que otro compilado sin **/fp: precisa**. **/ fp: precisa** deshabilita los intrínsecos; la biblioteca estándar de tiempo de ejecución se usan las rutinas en su lugar. Para obtener más información, consulte [/Oi (Generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md).

El siguiente comportamiento de punto flotante está habilitado con **/fp: precisa**:

- Contracciones: es decir, el uso de una operación compuesta que solo tiene un redondeo al final para reemplazar varias operaciones.

- Las optimizaciones de expresiones que no son válidas para valores especiales (NaN, +infinito, -infinito, +0, -0) no están permitidas. La optimizaciones de x-x = > 0, x * 0 = > 0, x-0 = > x, x + 0 = > x y 0 x = > - x no son válidas por diversas razones. (Vea IEEE 754 y el estándar C99).

- El compilador controla correctamente las comparaciones que implican NaN. Por ejemplo, x! = x se evalúa como **true** si `x` es NaN y las comparaciones ordenadas que implican NaN genere una excepción.

- La evaluación de la expresión se ajusta a C99 FLT_EVAL_METHOD=2, con la siguiente excepción: cuando se programa para procesadores x86, ya que la FPU se establece en una precisión de 53 bits, lo que se considera una precisión long-double.

- La multiplicación por 1,0 exactamente se transforma en un uso del otro factor. x * y\*1.0 se transforma en x\*y. De forma similar, x\*1.0\*y se transforma en x\*y.

- La división por 1,0 exactamente se transforma en un uso del dividendo. x * y/1.0 se transforma en x\*y. De forma similar, x / 1.0\*y se transforma en x\*y.

Uso de **/fp: precisa** cuando [fenv_access](../../preprocessor/fenv-access.md) es en deshabilita las optimizaciones, como evaluaciones en tiempo de compilación de expresiones de punto flotante. Por ejemplo, si usa [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) cambiar el modo de redondeo y el compilador efectúa un cálculo de punto flotante, el modo de redondeo especificado no está activada a menos que `fenv_access`es ON.

**/ fp: precisa** reemplaza el **/op.** opción del compilador.

#### <a name="fast"></a>Rápida

El **/fp: Fast** opción crea el código más rápido en la mayoría de los casos al relajar las reglas para optimizar las operaciones de punto flotante. Esto permite al compilador optimizar el código de punto flotante para mejorar la velocidad en detrimento de la precisión y la exactitud. Cuando **/fp: Fast** se especifica, el compilador no puede redondeo correctamente en instrucciones de asignación, conversiones de tipo o llamadas de función y no es posible que realice el redondeo de expresiones intermedias. El compilador puede reordenar las operaciones o realizar transformaciones algebraicas (por ejemplo, con arreglo a reglas asociativas y distributivas), sin que esto afecte a los resultados de precisión finita. El compilador puede cambiar las operaciones y los operandos a una precisión simple en lugar de seguir las reglas de promoción de tipos de C++. Las optimizaciones de contracción específicas de punto flotante siempre están habilitadas ([fp_contract](../../preprocessor/fp-contract.md) está activado). Excepciones de punto flotante y el acceso al entorno de FPU se deshabilitan (**/fp: excepto-** está implícito y [fenv_access](../../preprocessor/fenv-access.md) es OFF).

**/ fp: Fast** no se puede usar con **/fp: strict** o **/fp: precisa**. Se utiliza la última opción especificada en la línea de comandos. Si se especifica **/fp: Fast** y **/fp: excepto** genera un error del compilador.

Especificar [/Za, /Ze (deshabilitar extensiones de lenguaje)](../../build/reference/za-ze-disable-language-extensions.md) (compatibilidad con ANSI) y **/fp: Fast** puede provocar un comportamiento inesperado. Por ejemplo, las operaciones de punto flotante de precisión sencilla no se pueden redondear a precisión sencilla.

#### <a name="except"></a>Con la excepción

El **/fp: excepto** opción habilita un modelo confiable de excepción de punto flotante. Las excepciones se generan inmediatamente después de desencadenarse. Esta opción está desactivada de forma predeterminada. Al anexar un signo menos a la opción (**/fp: excepto-**) deshabilita de forma explícita.

#### <a name="strict"></a>strict

El **/fp: strict** opción habilita el modelo de punto flotante más estricto. **/ fp: strict** hace [fp_contract](../../preprocessor/fp-contract.md) sea OFF y [fenv_access](../../preprocessor/fenv-access.md) on. **/ fp: excepto** está implícito y se puede deshabilitar mediante la especificación explícita **/fp: excepto-**. Cuando se usa con **/fp: excepto-**, **/fp: strict** exige la semántica estricta de punto flotante, pero sin considerar eventos excepcionales.

## <a name="remarks"></a>Comentarios

Varios **/FP** opciones se pueden especificar en la misma compilación.

Para controlar el comportamiento de punto flotante por función, vea el [float_control](../../preprocessor/float-control.md) pragma. Esto invalida el **/FP** configuración del compilador. Como procedimiento de ingeniería aconsejable, se recomienda guardar y restaurar el comportamiento de punto flotante local:

```cpp
#pragma float_control(precise, on, push)
// Code that uses /fp:precise mode
#pragma float_control(pop)
```

La mayoría de las optimizaciones de punto flotante relacionadas con **/fp: strict**, **/fp: excepto** (y sus correspondientes directivas pragma) y el `fp_contract` pragma dependen del equipo. **/ fp: strict** y **/fp: excepto** no son compatibles con **/CLR**.

**/ fp: precisa** debería tratar la mayoría de los requisitos de punto flotante de la aplicación. Puede usar **/fp: excepto** y **/fp: strict**, pero puede haber cierto deterioro del rendimiento. Si el rendimiento es más importante, considere la posibilidad de usar **/fp: Fast**.

**/ fp: strict**, **/fp: Fast**, y **/fp: precisa** son modos de precisión (exactitud). Solo puede haber uno en vigor en un momento dado. Si ambos **/fp: strict** y **/fp: precisa** se especifican, el compilador usa el que procesa en último lugar. Ambos **/fp: strict** y **/fp: Fast** no se puede especificar.

Para obtener más información, consulte [optimización de punto flotante de Microsoft Visual C++](floating-point-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración** > **C o C++** > **generación de código** página de propiedades.

1. Modificar el **modelo de punto flotante** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador](compiler-options.md)
- [Establecer las opciones del compilador](setting-compiler-options.md)
- [Microsoft Visual C++, optimización de punto flotante](floating-point-optimization.md)