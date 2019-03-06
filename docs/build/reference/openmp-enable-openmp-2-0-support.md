---
title: /openmp (Habilitar la compatibilidad con OpenMP 2.0)
ms.date: 11/04/2016
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: bea51c7af41df666fd441555daa0d8d8387377ac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414140"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Habilitar la compatibilidad con OpenMP 2.0)

Hace que el compilador procese `#pragma` [omp](../../preprocessor/omp.md).

## <a name="syntax"></a>Sintaxis

```
/openmp
```

## <a name="remarks"></a>Comentarios

`#pragma omp` se usa para especificar [directivas](../../parallel/openmp/reference/openmp-directives.md) y [cláusulas](../../parallel/openmp/reference/openmp-clauses.md). Si **/OpenMP** no se especifica en una compilación, el compilador omite las cláusulas de OpenMP y directivas. [Función de OpenMP](../../parallel/openmp/reference/openmp-functions.md) la incluso si compilador procesa las llamadas **/OpenMP** no se especifica.

Las aplicaciones compiladas con **/OpenMP** y **/CLR** solo se pueden ejecutar en un proceso de dominio de aplicación único; no se admiten varios dominios de aplicación. Es decir, cuando se ejecuta el constructor de módulo (.cctor), lo detectará el proceso se compila con **/OpenMP** y si la aplicación se está cargando en un tiempo de ejecución no predeterminado. Para obtener más información, consulte [appdomain](../../cpp/appdomain.md), [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md), y [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).

Si intenta cargar una aplicación compilada con **/OpenMP** y **/CLR** en un dominio de aplicación no predeterminado, un <xref:System.TypeInitializationException> se producirá una excepción fuera del depurador y un Se producirá la excepción de OpenMPWithMultipleAppdomainsException en el depurador.

También se pueden generar estas excepciones en las situaciones siguientes:

- Si la aplicación compilada con **/CLR**, pero no con **/OpenMP**, se carga en un dominio de aplicación no predeterminado, pero donde el proceso incluye una aplicación que se compiló con **/ OpenMP**.

- Si se pasa la **/CLR** aplicación a una utilidad, como regasm.exe ([Regasm.exe (Assembly Registration Tool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), que carga los ensamblados de destino en un dominio de aplicación no predeterminado.

Seguridad de acceso del código de common language runtime no funciona en las regiones de OpenMP. Si aplica un atributo de seguridad de acceso de código CLR fuera de una región paralela, no entrarán en vigor en la región paralela.

Microsoft aconseja no escribir **/OpenMP** llamadores, uso de confianza de las aplicaciones que permite parcialmente <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, o cualquier atributo de seguridad de acceso de código CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **C o C++** nodo.

1. Seleccione el **lenguaje** página de propiedades.

1. Modificar el **la compatibilidad con OpenMP** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra algunos de los efectos del inicio de threadpool frente al uso de threadpool después de haberse iniciado. Suponiendo una x64, núcleo único, el grupo de subprocesos de procesador dual tarda unos 16 ms en iniciarse. Sin embargo después de que hay un costo muy pequeño para el grupo de subprocesos.

Cuando se compila con **/OpenMP**, la segunda llamada a test2 nunca se ejecuta ya que si se compila con **/openmp-**, ya que no hay ningún inicio de threadpool. En un millón de iteraciones del **/OpenMP** versión es más rápida que el **/openmp-** versión para la segunda llamada a test2 y a 25 iteraciones **/openmp-** y **/OpenMP** versiones register menor que la granularidad de reloj.

Por tanto, si tiene sólo un bucle en la aplicación y se ejecuta en menos de 15 ms (ajustado para la sobrecarga aproximada de la máquina), **/OpenMP** puede no ser adecuado, pero si es nada más que eso, puede considerar el uso de **/OpenMP**.

```
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

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
