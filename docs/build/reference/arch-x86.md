---
title: /arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: b1e5501f6edd3eb016395380ff476250c0c388b9
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816315"
---
# <a name="arch-x86"></a>/arch (x86)

Especifica la arquitectura para la generación de código en x86. Consulte también [/Arch (x64)](arch-x64.md) y [/Arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Argumentos

**/arch:IA32**<br/>
No especifica ninguna instrucción mejorada y también especifica x87 para los cálculos de punto flotante.

**/arch:SSE**<br/>
Habilita el uso de instrucciones SSE.

**/arch:SSE2**<br/>
Habilita el uso de instrucciones SSE2. Esta es la instrucción predeterminada en las plataformas x86 si no se especifica la opción **/Arch** .

**/arch:AVX**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.

**/arch:AVX2**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.

**/Arch: AVX512**<br/>
Habilita el uso de las instrucciones de las extensiones de vector avanzadas de Intel 512.

## <a name="remarks"></a>Comentarios

La opción **/Arch** habilita o deshabilita el uso de determinadas extensiones de conjunto de instrucciones, especialmente en el cálculo de vectores, disponibles en procesadores de Intel y AMD. En general, los procesadores que se introdujeron más recientemente pueden admitir extensiones adicionales sobre las que admiten procesadores anteriores, aunque debe consultar la documentación de un procesador determinado o probar la compatibilidad con la extensión del conjunto de instrucciones mediante [_ _ CPUID](../../intrinsics/cpuid-cpuidex.md) antes de ejecutar código mediante una extensión de conjunto de instrucciones.

**/Arch** solo afecta a la generación de código para las funciones nativas. Cuando se usa [/CLR](clr-common-language-runtime-compilation.md) para compilar, **/Arch** no tiene ningún efecto en la generación de código para las funciones administradas.

Las opciones **/Arch** hacen referencia a las extensiones del conjunto de instrucciones con las siguientes características:

- **Ia32** es el conjunto de instrucciones x86 de 32 bits heredado sin ninguna operación de vector y el uso de x87 para los cálculos de punto flotante.

- **SSE** permite el cálculo con vectores de hasta cuatro valores de punto flotante de precisión sencilla. También se agregaron las instrucciones de punto flotante correspondientes.

- **SSE2** permite el cálculo con vectores de 128 bits de valores enteros de precisión sencilla, doble precisión y 1, 2, 4 u 8 bytes. También se agregaron instrucciones escalares de precisión doble.

- **AVX** presentó una codificación de instrucciones alternativa para las instrucciones escalares de vectores y puntos flotantes que permite vectores de 128 bits o 256 bits, y ceros extiende todos los resultados vectoriales al tamaño del vector completo. (Para compatibilidad heredada, las instrucciones de vector de estilo SSE conservan todos los bits más allá del bit 127). La mayoría de las operaciones de punto flotante se extienden a 256 bits.

- **AVX2** extiende la mayoría de las operaciones de enteros a vectores de 256 bits y permite el uso de instrucciones de multiplicación y adición fusionadas (FMA).

- **AVX512** presentó otro formulario de codificación de instrucciones que permite vectores de 512 bits, además de otras características opcionales. También se han agregado instrucciones para operaciones adicionales.

El optimizador elige Cuándo y cómo usar las instrucciones de vectores en función del parámetro **/Arch** que se especifique. Los cálculos de punto flotante escalares se realizan con instrucciones SSE o AVX cuando están disponibles. Algunas convenciones de llamada especifican el paso de argumentos de punto flotante en la pila de x87 y, como resultado, el código puede utilizar una combinación de instrucciones de x87 y SSE/AVX para los cálculos de punto flotante. Las instrucciones de vector de entero también se pueden usar para algunas operaciones de enteros de 64 bits cuando están disponibles.

Además de las instrucciones escalares vectoriales y de punto flotante, cada opción **/Arch** también puede habilitar el uso de otras instrucciones que no son de vector asociadas a esa opción. Un ejemplo es la familia de instrucciones de CMOVcc que apareció por primera vez en los procesadores Intel Pentium Pro. Dado que las instrucciones de SSE se introdujeron con el procesador Intel Pentium III posterior, se pueden generar instrucciones CMOVcc excepto si se especifica **/Arch: ia32** .

Las operaciones de punto flotante normalmente se redondean a la precisión doble (64 bits) en código x87, pero puede usar `_controlfp` para modificar la palabra de control FP, incluida la configuración del control de precisión en precisión extendida (80 bits) o de precisión sencilla (32 bits). Para obtener más información, vea [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). SSE y AVX tienen instrucciones independientes de precisión sencilla y de doble precisión para cada operación, por lo que no hay ningún equivalente para el código SSE/AVX. Esto puede cambiar el modo en que los resultados se redondean cuando el resultado de una operación de punto flotante se usa directamente en el cálculo adicional en lugar de asignarlo a una variable de usuario. Considere el siguiente caso:

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Con asignación explícita:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/Arch** y [/QIfist](qifist-suppress-ftol.md) no se pueden usar en la misma operación de compilación. La opción **/QIfist** cambia el comportamiento de redondeo de la conversión de punto flotante a entero. El comportamiento predeterminado es truncar (redondear hacia cero), mientras que la opción **/QIfist** especifica el uso del modo de redondeo del entorno de punto flotante. Dado que esto cambia el comportamiento de todas las conversiones de punto flotante a entero, esta marca está en desuso. Al compilar para SSE o AVX, puede redondear un valor de punto flotante a un entero mediante el modo de redondeo de entorno de punto flotante mediante una secuencia de función intrínseca:

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

Las macros `_M_IX86_FP`, `__AVX__`, `__AVX2__`, `__AVX512F__`, `__AVX512CD__`, `__AVX512BW__`, `__AVX512DQ__` y `__AVX512VL__` indican qué opción del compilador **/Arch** se utilizó, si se usó alguna. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). La opción **/Arch: AVX2** y la macro `__AVX2__` se introdujeron en Visual Studio 2013 Update 2, versión 12.0.34567.1. La compatibilidad limitada con **/Arch: AVX512** se agregó en visual Studio 2017 y se amplió en visual Studio 2019.

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>Para establecer esta opción del compilador para AVX, AVX2, AVX512, IA32, SSE o SSE2 en Visual Studio

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la carpeta **propiedades de configuración**, **C/C++**  .

1. Seleccione la página de propiedades **generación de código** .

1. Modifique la propiedad **Habilitar conjunto de instrucciones mejorado** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
