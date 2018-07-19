---
title: -openmp (Habilitar soporte de OpenMP 2.0) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
dev_langs:
- C++
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe64011f48255a18aa8f8ccab7571533540a598a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378735"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Habilitar la compatibilidad con OpenMP 2.0)
Hace que el compilador pueda procesarlo `#pragma` [omp](../../preprocessor/omp.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/openmp  
```  
  
## <a name="remarks"></a>Comentarios  
 `#pragma omp` se utiliza para especificar [directivas](../../parallel/openmp/reference/openmp-directives.md) y [cláusulas](../../parallel/openmp/reference/openmp-clauses.md). Si **/OpenMP** no se especifica en una compilación, el compilador omite cláusulas de OpenMP y directivas. [Función de OpenMP](../../parallel/openmp/reference/openmp-functions.md) llamadas son procesadas por el incluso si compilador **/OpenMP** no se ha especificado.  
  
 Las aplicaciones compiladas con **/OpenMP** y **/CLR** sólo se puede ejecutar en un proceso de dominio de aplicación único; no se admiten varios dominios de aplicación. Es decir, cuando se ejecuta el constructor del módulo (.cctor), se detectarán el proceso se compila con **/OpenMP** y si la aplicación se está cargando en un tiempo de ejecución no predeterminado. Para obtener más información, consulte [appdomain](../../cpp/appdomain.md), [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), y [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).  
  
 Si intenta cargar una aplicación compilada con **/OpenMP** y **/CLR** en un dominio de aplicación no predeterminado, un <xref:System.TypeInitializationException> se producirá una excepción fuera del depurador y un Se producirá la excepción de OpenMPWithMultipleAppdomainsException en el depurador.  
  
 Estas excepciones también pueden generarse en las situaciones siguientes:  
  
-   Si la aplicación se compila con **/CLR**, pero no con **/OpenMP**, se carga en un dominio de aplicación no predeterminado pero donde el proceso incluye una aplicación que se compiló con **/ OpenMP**.  
  
-   Si se pasa el **/CLR** aplicación a una utilidad, como regasm.exe ([Regasm.exe (herramienta de registro de ensamblados)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), que carga sus ensamblados de destino en un dominio de aplicación no predeterminado.  
  
 Seguridad de acceso del código de common language runtime no funciona en regiones de OpenMP. Si aplica un atributo de seguridad de acceso a código CLR fuera de una región paralela, no estará en vigor en la región paralela.  
  
 Microsoft aconseja no escribir **/OpenMP** llamadores, uso de confianza de las aplicaciones que permite parcialmente <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, o los atributos de seguridad de acceso del código CLR.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **C/C++** nodo.  
  
4.  Seleccione el **lenguaje** página de propiedades.  
  
5.  Modificar el **la compatibilidad con OpenMP** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra algunos de los efectos del proceso de inicio de threadpool frente al uso de threadpool después de haberse iniciado. Suponiendo que un x64, núcleo único, procesador dual el grupo de subprocesos tarda unos 16 ms el inicio. Aunque después de que hay muy poco coste para el grupo de subprocesos.  
  
 Cuando se compila con **/OpenMP**, la segunda llamada a test2 nunca se ejecuta ya que si se compila con **/openmp-**, ya que no existe ningún inicio de grupo de subprocesos. En un millón de iteraciones el **/OpenMP** versión es más rápida que el **/openmp-** versión para la segunda llamada a test2 y a 25 iteraciones **/openmp-** y **/OpenMP** versiones register menor que la granularidad de reloj.  
  
 Por tanto, si tiene sólo un bucle en la aplicación y se ejecuta en menos de 15 ms (ajustado para la sobrecarga aproximada en su equipo), **/OpenMP** puede no ser adecuado, pero si es algo más que eso, puede que desee considerar el uso de **/OpenMP**.  
  
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
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)