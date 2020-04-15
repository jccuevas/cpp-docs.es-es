---
title: /openmp (Habilitar compatibilidad con OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336192"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (Habilitar compatibilidad con OpenMP)

Hace que el [`#pragma omp`](../../preprocessor/omp.md) compilador procese directivas en soporte de OpenMP.

## <a name="syntax"></a>Sintaxis

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__experimental__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Observaciones

`#pragma omp`se utiliza para especificar [Directivas](../../parallel/openmp/reference/openmp-directives.md) y [Cláusulas](../../parallel/openmp/reference/openmp-clauses.md). Si **/openmp** no se especifica en una compilación, el compilador omite las directivas y cláusulas OpenMP. El compilador procesa las llamadas a la [función OpenMP](../../parallel/openmp/reference/openmp-functions.md) incluso si no se especifica **/openmp.**

::: moniker range=">= vs-2019"

El compilador C++ admite actualmente el estándar OpenMP 2.0. Sin embargo, Visual Studio 2019 también ahora ofrece funcionalidad SIMD. Para usar SIMD, compile mediante la opción **/openmp:experimental.** Esta opción habilita las funciones habituales de OpenMP y las funciones adicionales de OpenMP SIMD no están disponibles cuando se utiliza el modificador **/openmp.**

::: moniker-end

Las aplicaciones compiladas mediante **/openmp** y **/clr** solo se pueden ejecutar en un único proceso de dominio de aplicación. No se admiten varios dominios de aplicación. Es decir, cuando se`.cctor`ejecuta el constructor de módulo ( ), detecta si el proceso se compila mediante **/openmp**y si la aplicación se carga en un tiempo de ejecución no predeterminado. Para obtener más información, vea [appdomain](../../cpp/appdomain.md), [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md)y [Initialization of Mixed Assemblies](../../dotnet/initialization-of-mixed-assemblies.md).

Si intenta cargar una aplicación compilada con **/openmp** y **/clr** en <xref:System.TypeInitializationException> un dominio de aplicación no `OpenMPWithMultipleAppdomainsException` predeterminado, se produce una excepción fuera del depurador y se produce una excepción en el depurador.

Estas excepciones también se pueden plantear en las siguientes situaciones:

- Si la aplicación se compila mediante **/clr** pero no **/openmp**y se carga en un dominio de aplicación no predeterminado, donde el proceso incluye una aplicación compilada con **/openmp**.

- Si pasa la aplicación **/clr** a una utilidad, como [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), que carga sus ensamblados de destino en un dominio de aplicación no predeterminado.

La seguridad de acceso al código de Common Language Runtime no funciona en las regiones de OpenMP. Si aplica un atributo de seguridad de acceso de código CLR fuera de una región paralela, no estará en vigor en la región paralela.

Microsoft no recomienda escribir aplicaciones **/openmp** que permitan llamadas de confianza parcial. No use <xref:System.Security.AllowPartiallyTrustedCallersAttribute>ni ningún atributo de seguridad de acceso al código CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda la página de propiedades **Propiedades** > de configuración**C/C++Language.** > **Language**

1. Modifique la propiedad **Soporte de OpenMP.**

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran algunos de los efectos del inicio del grupo de subprocesos frente al uso del grupo de subprocesos después de que se haya iniciado. Suponiendo un procesador dual x64, de un solo núcleo, el grupo de subprocesos tarda unos 16 ms en iniciarse. Después de eso, hay poco costo adicional para el grupo de subprocesos.

Cuando se compila con **/openmp**, la segunda llamada a test2 nunca se ejecuta más que si se compila con **/openmp-**, ya que no hay ningún inicio del grupo de subprocesos. En un millón de iteraciones, la versión **/openmp** es más rápida que la versión **/openmp-** para la segunda llamada a test2. En 25 iteraciones, las versiones **/openmp-** y **/openmp** registran menos que la granularidad del reloj.

Si solo tiene un bucle en la aplicación y se ejecuta en menos de 15 ms (ajustado para la sobrecarga aproximada en su máquina), **/openmp** puede no ser adecuado. Si es más alto, es posible que desee considerar el uso de **/openmp**.

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>Consulte también

[Opciones del compilador MSVC](compiler-options.md) \
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md) \
[OpenMP en MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
