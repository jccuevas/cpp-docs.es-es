---
title: "/fp (Especificar comportamiento de punto flotante) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.floatingPointModel"
  - "VC.Project.VCCLWCECompilerTool.FloatingPointExceptions"
  - "/fp"
  - "VC.Project.VCCLWCECompilerTool.floatingPointModel"
  - "VC.Project.VCCLCompilerTool.FloatingPointExceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/fp (opción del compilador) [C++]"
  - "-fp (opción del compilador) [C++]"
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# /fp (Especificar comportamiento de punto flotante)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el comportamiento de punto flotante en un archivo de código fuente.  
  
## Sintaxis  
  
```  
/fp:[precise | except[-] | fast | strict ]  
```  
  
## Marcas  
 **precise**  
 El valor predeterminado.  
  
 Mejora la coherencia de las pruebas de punto flotante de igualdad y desigualdad deshabilitando las optimizaciones que podrían cambiar la precisión de los cálculos de punto flotante. \(Es necesario mantener una precisión específica para preservar la compatibilidad estricta con ANSI\). De forma predeterminada, en el código de arquitecturas x86, el compilador utiliza los registros de 80 bits para mantener los resultados intermedios de los cálculos de punto flotante.  Esto aumenta la velocidad del programa y reduce su tamaño.  No obstante, dado que en el cálculo están involucrados tipos de datos de punto flotante que se representan en memoria con menos de 80 bits, utilizar los bits adicionales de precisión \(80 bits menos el número de bits de un tipo de punto flotante más pequeño\) en un cálculo laborioso puede generar resultados incoherentes.  
  
 Con **\/fp:precise** en procesadores x86, el compilador realiza el redondeo en las variables de tipo `float` hasta obtener la precisión adecuada para las asignaciones y conversiones de tipos y cuando se pasan parámetros a una función.  Este redondeo garantiza que los datos no tengan un valor más significativo que la capacidad de su tipo.  Un programa compilado con **\/fp:precise** puede ser más lento y mayor que otro compilado sin **\/fp:precise**.  **\/fp:precise** deshabilita los intrínsecos; en su lugar, se usan las rutinas de biblioteca en tiempo de ejecución estándar.  Para obtener más información, vea [\/Oi \(Generar funciones intrínsecas\)](../../build/reference/oi-generate-intrinsic-functions.md).  
  
 El siguiente comportamiento de punto flotante se habilita con **\/fp:precise**:  
  
-   Contracciones: es decir, el uso de una operación compuesta que solo tiene un redondeo al final para reemplazar varias operaciones.  
  
-   Las optimizaciones de expresiones que no son válidas para valores especiales \(NaN, \+infinito, \-infinito, \+0, \-0\) no están permitidas.  Las optimizaciones x\-x \=\> 0, x\*0 \=\> 0, x\-0 \=\> x, x\+0 \=\> x y 0\-x \=\> \-x no son válidas por varias razones. \(Vea IEEE 754 y el estándar C99\).  
  
-   El compilador controla correctamente las comparaciones que implican NaN.  Por ejemplo, x \!\= x se evalúa como **true** si `x` es NaN y las comparaciones ordenadas que implican NaN producen una excepción.  
  
-   La evaluación de la expresión se ajusta a C99 FLT\_EVAL\_METHOD\=2, con la siguiente excepción: cuando se programa para procesadores x86, ya que la FPU se establece en una precisión de 53 bits, lo que se considera una precisión long\-double.  
  
-   La multiplicación por 1,0 exactamente se transforma en un uso del otro factor.  x\*y\*1.0 se transforma en x\*y.  Del mismo modo, x\*1.0\*y se transforma en x\*y.  
  
-   La división por 1,0 exactamente se transforma en un uso del dividendo.  x\*y\/1.0 se transforma en x\*y.  Del mismo modo, x\/1.0\*y se transforma en x\*y.  
  
 Si se utiliza **\/fp:precise** cuando [fenv\_access](../../preprocessor/fenv-access.md) está establecido en ON, se deshabilitan las optimizaciones, como las evaluaciones en tiempo de compilación de expresiones de punto flotante.  Por ejemplo, si usa [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) para cambiar el modo de redondeo y el compilador efectúa un cálculo de punto flotante, el modo de redondeo especificado no tendrá efecto hasta que `fenv_access` se establezca en ON.  
  
 **\/fp:precise** reemplaza la opción del compilador **\/Op**.  
  
 **fast**  
 La mayoría de las veces, crea el código más rápido, ya que relaja las reglas para optimizar las operaciones de punto flotante.  Esto permite al compilador optimizar el código de punto flotante para mejorar la velocidad en detrimento de la precisión y la exactitud.  Cuando se especifica **\/fp:fast**, es posible que el compilador no realice el redondeo correctamente en instrucciones de asignación, conversiones de tipo o llamadas a funciones, y que no realice el redondeo de expresiones intermedias.  El compilador puede reordenar las operaciones o realizar transformaciones algebraicas \(por ejemplo, con arreglo a reglas asociativas y distributivas\), sin que esto afecte a los resultados de precisión finita.  El compilador puede cambiar las operaciones y los operandos a una precisión simple en lugar de seguir las reglas de promoción de tipos de C\+\+.  Las optimizaciones de contracción específicas de punto flotante siempre están habilitadas \([fp\_contract](../../preprocessor/fp-contract.md) está establecido en ON\).  Las excepciones de punto flotante y el acceso al entorno de la FPU se deshabilitan \(**\/fp:except\-** está implícito y [fenv\_access](../../preprocessor/fenv-access.md) está establecido en OFF\).  
  
 No se puede utilizar **\/fp:fast** con **\/fp:strict** o **\/fp:precise**.  Se utiliza la última opción especificada en la línea de comandos.  Si se especifica **\/fp:fast** y **\/fp:except**, se genera un error del compilador.  
  
 Si se especifica [\/Za, \/Ze \(Deshabilitar extensiones de lenguaje\)](../../build/reference/za-ze-disable-language-extensions.md) \(compatibilidad con ANSI\) y **\/fp:fast**, puede producirse un comportamiento inesperado.  Por ejemplo, las operaciones de punto flotante de precisión sencilla no se pueden redondear a precisión sencilla.  
  
 **except\[\-\]**  
 Modelo confiable de excepción de punto flotante.  Las excepciones se generan inmediatamente después de desencadenarse.  Esta opción está desactivada de forma predeterminada.  Al anexar explícitamente un signo menos a la opción, se deshabilita.  
  
 **strict**  
 Modelo de punto flotante más estricto.  **\/fp:strict** hace que [fp\_contract](../../preprocessor/fp-contract.md) tenga el valor OFF y [fenv\_access](../../preprocessor/fenv-access.md) el valor ON.  **\/fp:except** está implícito y se puede deshabilitar explícitamente si se especifica **\/fp:except\-**.  Cuando se utiliza con **\/fp:except\-**, **\/fp:strict** fuerza la semántica de punto flotante estricta, pero sin considerar eventos excepcionales.  
  
## Comentarios  
 En una misma compilación, se pueden especificar varias opciones de **\/fp**.  
  
 Para controlar el comportamiento de punto flotante por función, vea la directiva pragma [float\_control](../../preprocessor/float-control.md).  Esto reemplaza la configuración del compilador **\/fp**.  Como procedimiento de ingeniería aconsejable, se recomienda guardar y restaurar el comportamiento de punto flotante local:  
  
```css  
#pragma float_control(precise, on, push)  
// Code that uses /fp:precise mode  
#pragma float_control(pop)  
```  
  
 La mayoría de las optimizaciones de punto flotante relacionadas con **\/fp:strict**, **\/fp:except** \(y sus correspondientes directivas pragma\) y la directiva pragma `fp_contract` dependen del equipo.  **\/fp:strict** y **\/fp:except** no son compatibles con **\/clr**.  
  
 **\/fp:precise** debería tratar la mayoría de los requisitos de punto flotante de una aplicación.  Puede usar **\/fp:except** y **\/fp:strict**, pero el rendimiento podría disminuir.  Si el rendimiento es muy importante, considere la posibilidad de usar **\/fp:fast**.  
  
 **\/fp:strict**, **\/fp:fast** y **\/fp:precise** son modos de precisión \(exactitud\).  Solo puede haber uno en vigor en un momento dado.  Si tanto **\/fp:strict** como **\/fp:precise** están especificados, el compilador usa el que se procesa en último lugar.  No se puede especificar **\/fp:strict** y **\/fp:fast** a la vez.  
  
 Para obtener más información, vea la página sobre la [optimización de punto flotante de Microsoft Visual C\+\+](http://msdn.microsoft.com/library/aa289157.aspx).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **C\/C\+\+**.  
  
4.  Seleccione la página de propiedades **Generación de código**.  
  
5.  Modifique la propiedad **Modelo de punto flotante**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Optimización de punto flotante en Microsoft Visual C\+\+](http://msdn.microsoft.com/library/aa289157.aspx)