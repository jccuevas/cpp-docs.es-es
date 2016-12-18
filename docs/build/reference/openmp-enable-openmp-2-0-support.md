---
title: "/openmp (Habilitar la compatibilidad con OpenMP 2.0) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/openmp"
  - "VC.Project.VCCLCompilerTool.OpenMP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/openmp (opción del compilador) [C++]"
  - "-openmp (opción del compilador) [C++]"
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /openmp (Habilitar la compatibilidad con OpenMP 2.0)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace que el compilador procese `#pragma`[omp](../../preprocessor/omp.md).  
  
## Sintaxis  
  
```  
/openmp  
```  
  
## Comentarios  
 `#pragma omp` se utiliza para especificar [Directives](../../parallel/openmp/reference/openmp-directives.md) y [Clauses](../../parallel/openmp/reference/openmp-clauses.md).  Si **\/openmp** no se especifica en una compilación, el compilador omite cláusulas y directivas de OpenMP.  El compilador procesa las llamadas a la [función de OpenMP](../../parallel/openmp/reference/openmp-functions.md) aun cuando no se haya especificado **\/openmp**.  
  
 Una aplicación compilada con **\/openmp** y que utiliza [Libraries](../../parallel/openmp/reference/openmp-libraries.md) sólo se puede ejecutar en Windows 2000 o sistemas operativos posteriores.  
  
 Las aplicaciones compiladas con **\/openmp** y **\/clr** sólo se pueden ejecutar en un único proceso del dominio de aplicación; no se admiten varios dominios de aplicación.  Es decir, cuando se ejecuta el constructor del módulo \(.cctor\), detecta que el proceso se compila con **\/openmp** y si la aplicación se está cargando en un tiempo de ejecución no predeterminado.  Para obtener más información, vea [appdomain](../../cpp/appdomain.md), [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) y [Inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md).  
  
 Si intenta cargar una aplicación compilada con **\/openmp** y **\/clr** en un dominio de aplicación no predeterminado, se producirá una excepción <xref:System.TypeInitializationException> fuera del depurador y otra excepción OpenMPWithMultipleAppdomainsException en el depurador.  
  
 Estas excepciones también se pueden producir en las situaciones siguientes:  
  
-   Si la aplicación compilada con **\/clr**, pero no con **\/openmp**, se carga en un dominio de aplicación no predeterminado pero donde el proceso incluye una aplicación que se compiló con **\/openmp**.  
  
-   Si pasa la aplicación de **\/clr** a una utilidad, como regasm.exe \([Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)\), que carga sus ensamblados de destino en un dominio de aplicación no predeterminado.  
  
 La seguridad de acceso del código de Common Language Runtime \(CLR\) no trabaja en regiones de OpenMP.  Si aplica un atributo de seguridad de acceso del código de CLR fuera de una región paralela, no estará en vigor en la región paralela.  
  
 Microsoft aconseja no escribir aplicaciones de **\/openmp** que permitan llamadores parcialmente de confianza, utilizando <xref:System.Security.AllowPartiallyTrustedCallersAttribute> o cualquier atributo de seguridad de acceso del código de CLR.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **C\/C\+\+**.  
  
4.  Seleccione la página de propiedades **Lenguaje**.  
  
5.  Modifique la propiedad **Compatibilidad con OpenMP**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.  
  
## Ejemplo  
 El ejemplo siguiente muestra algunos de los efectos de iniciar un grupo de subprocesos frente a utilizar el grupo de subprocesos después de haberse iniciado.  Suponiendo x64, núcleo único, procesador dual, el grupo de subprocesos tarda unos 16 ms en iniciarse.  No obstante, después hay un costo muy pequeño para el grupo de subprocesos.  
  
 Cuando se compila con **\/openmp**, la segunda llamada a test2 nunca se ejecuta durante más tiempo que si se compila con **\/openmp\-**, ya que no hay que iniciar un grupo de subprocesos.  A un millón de iteraciones, la versión de **\/openmp** es más rápida que la de **\/openmp\-** para la segunda llamada a test2, y a 25 iteraciones, tanto la versión de **\/openmp\-** como la de **\/openmp** registran tiempos menores.  
  
 Así pues, si sólo hay un bucle en la aplicación y se ejecuta en menos de 15 ms \(ajustado para la sobrecarga aproximada de su equipo\), **\/openmp** podría no ser apropiado, pero si tarda un poco más, entonces podría considerar el uso de **\/openmp**.  
  
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
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)