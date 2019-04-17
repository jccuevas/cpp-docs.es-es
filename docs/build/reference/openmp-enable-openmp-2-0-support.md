---
title: /OpenMP (habilitar la compatibilidad con OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: caa06d89c590abd2b3a74a5a6b118d6ba4acd910
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674271"
---
# <a name="openmp-enable-openmp-support"></a>/OpenMP (habilitar la compatibilidad con OpenMP)

Hace que el compilador procese [ `#pragma omp` ](../../preprocessor/omp.md) directivas en apoyo de OpenMP.

## <a name="syntax"></a>Sintaxis

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__experimental__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Comentarios

`#pragma omp` se usa para especificar [directivas](../../parallel/openmp/reference/openmp-directives.md) y [cláusulas](../../parallel/openmp/reference/openmp-clauses.md). Si **/OpenMP** no se especifica en una compilación, el compilador omite las cláusulas de OpenMP y directivas. [Función de OpenMP](../../parallel/openmp/reference/openmp-functions.md) la incluso si compilador procesa las llamadas **/OpenMP** no se especifica.

::: moniker range=">= vs-2019"

El C++ compilador es compatible actualmente con el estándar OpenMP 2.0. Sin embargo, Visual Studio de 2019 ahora también ofrece funcionalidad SIMD. Para usar SIMD, compilar mediante la **/OpenMP: experimental** opción. Esta opción permite que tanto las características habituales de OpenMP y OpenMP SIMD características adicionales no están disponibles cuando se usa el **/OpenMP** cambie.

::: moniker-end

Las aplicaciones compiladas con ambos métodos **/OpenMP** y **/CLR** solo se pueden ejecutar en un proceso de dominio de aplicación único. No se admiten varios dominios de aplicación. Es decir, cuando el constructor de módulo (`.cctor`) es ejecutar, detecta si el proceso se ha compilado mediante **/OpenMP**, y si la aplicación se carga en un tiempo de ejecución no predeterminado. Para obtener más información, consulte [appdomain](../../cpp/appdomain.md), [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md), y [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).

Si intenta cargar una aplicación compilada con ambos **/OpenMP** y **/CLR** en un dominio de aplicación no predeterminado, un <xref:System.TypeInitializationException> excepción fuera del depurador y un `OpenMPWithMultipleAppdomainsException` excepción se produce en el depurador.

También se pueden generar estas excepciones en las situaciones siguientes:

- Si la aplicación se compila con **/CLR** pero no **/OpenMP**y se carga en un dominio de aplicación no predeterminado, donde el proceso incluye una aplicación compilada mediante   **/OpenMP**.

- Si se pasa la **/CLR** aplicación a una utilidad, como [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), que carga los ensamblados de destino en un dominio de aplicación no predeterminado.

Seguridad de acceso del código de common language runtime no funciona en las regiones de OpenMP. Si aplica un atributo de seguridad de acceso de código CLR fuera de una región paralela, no entrarán en vigor en la región paralela.

Microsoft no recomienda escribir **/OpenMP** llamadores de confianza de aplicaciones que permiten parcialmente. No use <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, o cualquier atributo de seguridad de acceso de código CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el **propiedades de configuración** > **C /C++** > **lenguaje** página de propiedades.

1. Modificar el **la compatibilidad con OpenMP** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra algunos de los efectos del inicio del grupo de subprocesos frente al uso del grupo de subprocesos después de haberse iniciado. Suponiendo que x64, núcleo único, procesador dual, el grupo de subprocesos tarda aproximadamente 16 ms en iniciarse. Después de eso, allí es poco coste adicional para el grupo de subprocesos.

Cuando se compila utilizando **/OpenMP**, la segunda llamada a test2 nunca se ejecuta ya que si se compila mediante **/openmp-**, ya que no hay ningún inicio de grupo de subprocesos. En un millón de iteraciones, el **/OpenMP** versión es más rápida que el **/openmp-** versión para la segunda llamada a test2. En 25 iteraciones, ambos **/openmp-** y **/OpenMP** versiones register menor que la granularidad de reloj.

Si tiene sólo un bucle en la aplicación y se ejecuta en menos de 15 ms (ajustados para la sobrecarga aproximada de la máquina), **/OpenMP** puede no ser adecuado. Si es mayor, es posible que desee considerar el uso **/OpenMP**.

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

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md) \
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md) \
[OpenMP en MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
