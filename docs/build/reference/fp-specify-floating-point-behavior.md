---
title: /fp (Especificar comportamiento de punto flotante)
ms.date: 11/09/2018
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
ms.openlocfilehash: 402b59c4aee34a413a08235aab2327ca64e7db39
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439682"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Especificar comportamiento de punto flotante)

Especifica cómo el compilador trata las excepciones, optimizaciones y expresiones de punto flotante. Las opciones de **/FP** especifican si el código generado permite realizar cambios en el entorno de punto flotante en el modo de redondeo, las máscaras de excepción y el comportamiento subnormal, y si las comprobaciones de estado de punto flotante devuelven resultados actuales y precisos. Controla si el compilador genera código que mantiene la operación de origen y el orden de las expresiones, y se ajusta al estándar para la propagación de NaN, o bien, si en su lugar genera código más eficaz que puede reordenar o combinar operaciones y usar la simplificación transformaciones algebraicas no permitidas por el estándar.

## <a name="syntax"></a>Sintaxis

> **/FP:** [**precisión** | **STRICT** | **Fast** | **excepto**[ **-** ]]

### <a name="arguments"></a>Argumentos

#### <a name="precise"></a>cifras

De forma predeterminada, el compilador usa el comportamiento de `/fp:precise`.

En `/fp:precise` el compilador conserva el orden de las expresiones de origen y las propiedades de redondeo del código de punto flotante al generar y optimizar el código de objeto para el equipo de destino. El compilador se redondea a la precisión del código fuente en cuatro puntos específicos durante la evaluación de expresiones: en las asignaciones, en conversiones, cuando se pasa un argumento de punto flotante a una llamada de función, y cuando un valor de punto flotante se devuelve de una llamada de función. Los cálculos intermedios se pueden realizar en la precisión de la máquina. Conversiones se puede usar para redondear de forma explícita los cálculos intermedios.

El compilador no realiza transformaciones algebraicas en expresiones de punto flotante, como la reasociación o la distribución, a menos que se garantice que la transformación genera un resultado idéntico bit a bit.
Las expresiones que implican valores especiales (NaN, + infinito,-Infinity,-0,0) se procesan de acuerdo con las especificaciones IEEE-754. Por ejemplo, `x != x` se evalúa como **true** si x es Nan. Los *contratos*de punto flotante, es decir, las instrucciones máquina que combinan operaciones de punto flotante, se pueden generar en `/fp:precise`.

El compilador genera código diseñado para ejecutarse en el [entorno de punto flotante predeterminado](#the-default-floating-point-environment) y da por supuesto que no se tiene acceso al entorno de punto flotante ni se modifica en tiempo de ejecución. Es decir, se supone que el código no desenmascara las excepciones de punto flotante, los registros de estado de punto flotante de lectura o escritura o los modos de redondeo.

Si el código de punto flotante no depende del orden de las operaciones y expresiones en las instrucciones de punto flotante (por ejemplo, si no le importa si `a * b + a * c` se calcula como `(b + c) * a` o `2 * a` como `a + a`), tenga en cuenta la opción [/FP: Fast](#fast) , que puede generar código más rápido y eficaz. Si el código depende del orden de las operaciones y de las expresiones, y obtiene acceso o modifica el entorno de punto flotante (por ejemplo, para cambiar los modos de redondeo o para interceptar las excepciones de punto flotante), use [/FP: STRICT](#strict).

#### <a name="strict"></a>strict

`/fp:strict` tiene un comportamiento similar al de `/fp:precise`, es decir, el compilador conserva las propiedades de ordenación de origen y redondeo del código de punto flotante cuando genera y optimiza el código de objeto para el equipo de destino, y observa el estándar al controlar los valores especiales. Además, el programa puede tener acceso o modificar de forma segura el entorno de punto flotante en tiempo de ejecución.

En `/fp:strict`, el compilador genera código que permite al programa desenmascarar de forma segura las excepciones de punto flotante, leer o escribir registros de estado de punto flotante o cambiar los modos de redondeo. Se redondea a la precisión del código fuente en cuatro puntos específicos durante la evaluación de expresiones: en las asignaciones, en conversiones, cuando se pasa un argumento de punto flotante a una llamada de función, y cuando un valor de punto flotante se devuelve de una llamada de función. Los cálculos intermedios se pueden realizar en la precisión de la máquina. Conversiones se puede usar para redondear de forma explícita los cálculos intermedios. El compilador no realiza transformaciones algebraicas en expresiones de punto flotante, como la reasociación o la distribución, a menos que se garantice que la transformación genera un resultado idéntico bit a bit. Las expresiones que implican valores especiales (NaN, + infinito,-Infinity,-0,0) se procesan de acuerdo con las especificaciones IEEE-754. Por ejemplo, `x != x` se evalúa como **true** si x es Nan. Los contratos de punto flotante no se generan en `/fp:strict`.

`/fp:strict` es computacionalmente más caro que `/fp:precise` porque el compilador debe insertar instrucciones adicionales para interceptar excepciones y permitir que los programas tengan acceso o modifiquen el entorno de punto flotante en tiempo de ejecución. Si el código no usa esta capacidad, pero requiere la ordenación y el redondeo del código fuente, o si se basa en valores especiales, use `/fp:precise`. En caso contrario, considere la posibilidad de usar `/fp:fast`, que puede generar código más rápido y más pequeño.

#### <a name="fast"></a>fast

La opción `/fp:fast` permite al compilador reordenar, combinar o simplificar las operaciones de punto flotante para optimizar el código de punto flotante para la velocidad y el espacio. El compilador puede omitir el redondeo en instrucciones de asignación, conversiones o llamadas de función. Puede reordenar las operaciones o realizar transformaciones algebraicas, por ejemplo, mediante el uso de las leyes asociativas y distributivo, aunque dichas transformaciones tengan como resultado un comportamiento de redondeo perceptiblemente diferente. Debido a esta optimización mejorada, el resultado de algunos cálculos de punto flotante puede diferir de los producidos por otras opciones de `/fp`. Es posible que los valores especiales (NaN, + infinito,-Infinity,-0,0) no se propaguen o se comporten de forma estricta según el estándar IEEE-754. Los contratos de punto flotante se pueden generar en `/fp:fast`. El compilador sigue estando enlazado por la arquitectura subyacente en `/fp:fast`y las optimizaciones adicionales pueden estar disponibles mediante el uso de la opción [/Arch](arch-minimum-cpu-architecture.md) .

En `/fp:fast`, el compilador genera código diseñado para ejecutarse en el entorno de punto flotante predeterminado y da por supuesto que no se tiene acceso al entorno de punto flotante ni se ha modificado en tiempo de ejecución. Es decir, se supone que el código no desenmascara las excepciones de punto flotante, los registros de estado de punto flotante de lectura o escritura o los modos de redondeo.

`/fp:fast` está pensada para programas que no requieren la ordenación estricta de código fuente y el redondeo de expresiones de punto flotante, y no confían en las reglas estándar para controlar valores especiales como NaN. Si el código de punto flotante requiere la preservación de la ordenación y el redondeo del código fuente, o se basa en el comportamiento estándar de los valores especiales, use [/FP: precise](#precise). Si el código tiene acceso al entorno de punto flotante o lo modifica para cambiar los modos de redondeo, desenmascarar las excepciones de punto flotante o comprobar el estado de punto flotante, use [/FP: STRICT](#strict).

#### <a name="except"></a>CEPT

La opción `/fp:except` genera código para garantizar que todas las excepciones de punto flotante sin máscara se desencadenen en el punto exacto en el que se producen, y que no se genera ninguna excepción de punto flotante adicional. De forma predeterminada, la opción `/fp:strict` habilita `/fp:except`y `/fp:precise` no. La opción `/fp:except` no es compatible con `/fp:fast`. La opción se puede deshabilitar explícitamente de `/fp:except-`.

Tenga en cuenta que `/fp:except` no habilita ninguna excepción de punto flotante por sí misma, pero es necesaria para que los programas habiliten las excepciones de punto flotante. Consulte [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) para obtener información sobre cómo habilitar las excepciones de punto flotante.

## <a name="remarks"></a>Observaciones

Se pueden especificar varias opciones de `/fp` en la misma línea de comandos del compilador. Solo una de las opciones `/fp:strict`, `/fp:fast`y `/fp:precise` puede estar en vigor a la vez. Si se especifica más de una de estas opciones en la línea de comandos, la opción más adelante tendrá prioridad y el compilador generará una advertencia. Las opciones `/fp:strict` y `/fp:except` no son compatibles con `/clr`.

La opción [/za](za-ze-disable-language-extensions.md) (compatibilidad con ANSI) no es compatible con `/fp`.

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>Usar directivas de compilador para controlar el comportamiento de punto flotante

El compilador proporciona tres directivas pragma para invalidar el comportamiento de punto flotante especificado en la línea de comandos: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md)y [fp_contract](../../preprocessor/fp-contract.md). Puede usar estas directivas para controlar el comportamiento de punto flotante en el nivel de función, no dentro de una función. Tenga en cuenta que estas directivas no se corresponden directamente con las opciones de `/fp`. En esta tabla se muestra cómo se asignan entre sí las opciones de `/fp` y las directivas pragma. Para obtener más información, vea la documentación de las opciones individuales y las directivas pragma.

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|apagado|apagado|apagado|en|
|`/fp:precise`|en|apagado|apagado|en|
|`/fp:strict`|en|en|en|apagado|

### <a name="the-default-floating-point-environment"></a>El entorno de punto flotante predeterminado

Cuando se inicializa un proceso, se establece el *entorno de punto flotante predeterminado* . Este entorno enmascara todas las excepciones de punto flotante, establece el modo de redondeo en redondear a la más cercana (`FE_TONEAREST`), conserva los valores subnormales (desnormalizados), usa la precisión predeterminada de mantisa (mantisa) para los valores **float**, **Double**y **Long Double** , y si es compatible, establece el control de infinito en el modo de afinidad predeterminado.

### <a name="floating-point-environment-access-and-modification"></a>Acceso y modificación del entorno de punto flotante

Microsoft Visual C++ Runtime proporciona varias funciones para tener acceso al entorno de punto flotante y modificarlo. Entre ellas se incluyen [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)y [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) y sus variantes. Para garantizar el comportamiento correcto del programa cuando el código obtiene acceso o modifica el entorno de punto flotante, `fenv_access` debe estar habilitado, ya sea mediante la opción `/fp:strict` o mediante el uso de la `fenv_access` pragma, para que estas funciones surtan efecto. Cuando `fenv_access` no está habilitado, el acceso o la modificación del entorno de punto flotante puede dar lugar a un comportamiento inesperado del programa: es posible que el código no respete los cambios solicitados en el entorno de punto flotante. es posible que los registros de estado de punto flotante no informen de los resultados esperados o actuales; y pueden producirse excepciones de punto flotante inesperadas o puede que no se produzcan excepciones de punto flotante.

Cuando el código tenga acceso al entorno de punto flotante o lo modifique, debe tener cuidado al combinar el código donde `fenv_access` está habilitado con código que no tiene `fenv_access` habilitado. En el código en el que `fenv_access` no está habilitado, el compilador supone que el entorno de punto flotante predeterminado de la plataforma está en vigor y que no se tiene acceso al estado de punto flotante ni se ha modificado. Se recomienda guardar y restaurar el entorno de punto flotante local a su estado predeterminado antes de que el control se transfiera a una función que no tiene `fenv_access` habilitado. En este ejemplo se muestra cómo se puede establecer y restaurar el pragma `float_control`:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Modos de redondeo de punto flotante

En ambos `/fp:precise` y `/fp:fast` el compilador genera código diseñado para ejecutarse en el entorno de punto flotante predeterminado y presupone que no se tiene acceso al entorno ni se ha modificado en tiempo de ejecución. Es decir, se supone que el código no desenmascara las excepciones de punto flotante, los registros de estado de punto flotante de lectura o escritura o los modos de redondeo.  Sin embargo, algunos programas deben modificar el entorno de punto flotante. Por ejemplo, en este ejemplo se calculan los límites de error de una multiplicación de punto flotante mediante la modificación de los modos de redondeo de punto flotante:

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

Dado que el compilador asume el entorno de punto flotante predeterminado en `/fp:fast` y `/fp:precise` es libre de omitir las llamadas a `_controlfp_s`. Por ejemplo, cuando se compila con `/O2` y `/fp:precise` para la arquitectura x86, los límites no se calculan y el programa de ejemplo genera:

```Output
cLower = -inf
cUpper = -inf
```

Cuando se compila con `/O2` y `/fp:strict` para la arquitectura x86, el programa de ejemplo genera:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Valores especiales de punto flotante

En `/fp:precise` y `/fp:strict`, las expresiones que implican valores especiales (NaN, + infinito,-Infinity,-0,0) se comportan de acuerdo con las especificaciones IEEE-754. En `/fp:fast`, el comportamiento de estos valores especiales puede ser incoherente con IEEE-754.

Este ejemplo muestra el comportamiento diferente de los valores especiales en `/fp:precise`, `/fp:strict` y `/fp:fast`:

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

Cuando se compila con `/O2` `/fp:precise` o `/O2` `/fp:strict` para la arquitectura x86, las salidas son coherentes con la especificación IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Cuando se compila con `/O2` `/fp:fast` para la arquitectura x86, las salidas no son coherentes con IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Transformaciones algebraicos de punto flotante

En `/fp:precise` y `/fp:strict`, el compilador no realiza transformaciones matemáticas a menos que se garantice que la transformación genera un resultado idéntico bit a bit. El compilador puede realizar dichas transformaciones en `/fp:fast`. Por ejemplo, la expresión `a * b + a * c` en la función de ejemplo `algebraic_transformation` se puede compilar en `a * (b + c)` en `/fp:fast`. Dichas transformaciones no se realizan en `/fp:precise` o `/fp:strict`, y el compilador genera `a * b + a * c`.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Puntos de conversión explícitos de punto flotante

En `/fp:precise` y `/fp:strict`, el compilador se redondea a la precisión del código fuente en cuatro puntos específicos durante la evaluación de expresiones: en las asignaciones, en conversiones, cuando se pasa un argumento de punto flotante a una llamada de función, y cuando un valor de punto flotante se devuelve de una llamada de función. Conversiones se puede usar para redondear de forma explícita los cálculos intermedios. En `/fp:fast`, el compilador no genera conversiones explícitas en estos puntos para garantizar la precisión del código fuente. Este ejemplo muestra el comportamiento en diferentes opciones de `/fp`:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Cuando se compila con `/O2` `/fp:precise` o `/O2` `/fp:strict`, puede ver que las conversiones de tipos explícitas se insertan en la conversión y en el punto de retorno de la función en el código generado para la arquitectura x64:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

En `/O2` `/fp:fast` se simplifica el código generado, ya que todas las conversiones de tipo están optimizadas:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > página de propiedades **generación de código** de **C/C++**  > .

1. Modifique la propiedad **modelo de punto flotante** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
 