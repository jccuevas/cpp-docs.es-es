---
title: "Procedimientos recomendados para la optimizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Visual C++, optimización"
  - "optimización, procedimientos recomendados"
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Procedimientos recomendados para la optimizaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describen algunos procedimientos recomendados para la optimización en Visual C\+\+.  Se tratan los temas siguientes:  
  
-   Opciones del compilador y del vinculador  
  
    -   Optimización guiada por perfiles  
  
    -   ¿Qué nivel de optimización debería utilizar?  
  
    -   Modificadores de punto flotante  
  
-   Modificadores declspec de optimización  
  
-   Directivas pragma de optimización  
  
-   \_\_restrict y \_\_assume  
  
-   Compatibilidad intrínseca  
  
-   Excepciones  
  
## Opciones del compilador y del vinculador  
  
### Optimización guiada por perfiles  
 Visual C\+\+ admite la Optimización guiada por perfiles \(PGO\).  Esta optimización utiliza datos de perfil de ejecuciones anteriores de una versión instrumentada de una aplicación para controlar la optimización posterior de la aplicación.  La utilización de PGO puede ocupar mucho tiempo; por tanto, no lo deberían utilizar todos los desarrolladores, sino que se recomienda utilizar PGO para la versión de lanzamiento final de un producto.  Para obtener más información, vea [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md).  
  
 Además, se ha mejorado la optimización de todo el programa \(que también se conoce como generación de código en tiempo de vínculo\) y las optimizaciones **\/O1** y **\/O2**.  En general, una aplicación compilada con una de estas opciones es más rápida que la misma aplicación compilada con un compilador anterior.  
  
 Para obtener más información, vea [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md) y [\/O1, \/O2 \(Minimizar tamaño, maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).  
  
### ¿Qué nivel de optimización debería utilizar?  
 Si es posible, las últimas versiones de lanzamiento se deberían compilar con las optimizaciones guiadas por perfiles.  Si no es posible generar con PGO, ya sea debido a una infraestructura insuficiente para ejecutar las compilaciones instrumentadas, o bien por no tener acceso a los escenarios, se recomienda realizar la generación con la optimización de todo el programa.  
  
 El modificador **\/Gy** también resulta muy útil.  Genera un COMDAT independiente para cada función, dando más flexibilidad al vinculador cuando quita COMDAT sin referencia y plegamiento de COMDAT.  La única desventaja de utilizar **\/Gy** es que puede tener un efecto secundario en tiempo de compilación.  Por consiguiente, por lo general se recomienda utilizarlo.  Para obtener más información, vea [\/Gy \(Habilitar vinculación en el nivel de función\)](../../build/reference/gy-enable-function-level-linking.md).  
  
 Para vincular en entornos de 64 bits, se recomendaba utilizar la opción del vinculador **\/OPT:REF,ICF** y, en entornos de 32 bits, se recomienda **\/OPT:REF**.  Para obtener más información, vea [\/OPT \(Optimizaciones\)](../../build/reference/opt-optimizations.md).  
  
 También se recomienda encarecidamente generar símbolos de depuración, incluso con versiones de lanzamiento optimizadas.  No afecta al código generado y facilita la depuración de la aplicación, si fuera necesario.  
  
### Modificadores de punto flotante  
 La opción **\/Op** del compilador se ha quitado y se han agregado las cuatro opciones del compilador siguientes que tratan de optimizaciones de punto flotante:  
  
|||  
|-|-|  
|**\/fp:precise**|Ésta es la recomendación predeterminada y se debería utilizar en la mayoría de los casos.|  
|**\/fp:fast**|Se recomienda si el rendimiento es de la máxima importancia; por ejemplo, en juegos.  Dará como resultado un rendimiento mucho más rápido.|  
|**\/fp:strict**|Se recomienda si necesitan excepciones en punto flotante y si se desea el comportamiento IEEE.  Dará como resultado el rendimiento más lento.|  
|**\/fp:except\[\-\]**|Se puede utilizar junto con **\/fp:strict** o **\/fp:precise**, pero no con **\/fp:fast**.|  
  
 Para obtener más información, vea [\/fp \(Especificar comportamiento de punto flotante\)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
## Modificadores declspec de optimización  
 En esta sección, se examinarán dos modificadores declspec que se pueden utilizar en programas para mejorar el rendimiento: `__declspec(restrict)` y `__declspec(noalias)`.  
  
 El modificador declspec `restrict` sólo se puede aplicar a declaraciones de función que devuelven un puntero, como `__declspec(restrict) void *malloc(size_t size);`  
  
 El modificador declspec `restrict` se utiliza en funciones que devuelven punteros sin alias.  Esta palabra clave se utiliza para la implementación de la biblioteca en tiempo de ejecución de C de `malloc` ya que nunca devolverá un valor de puntero que se esté utilizando en el programa actual \(salvo que se esté haciendo algo no válido, como utilizar la memoria después de liberarla\).  
  
 El modificador declspec `restrict` da más información al compilador para realizar las optimizaciones del compilador.  Una de las tareas que más le cuesta al compilador es determinar qué punteros son alias de otros punteros y esta información ayuda considerablemente al compilador.  
  
 Merece la pena indicar que es una sugerencia para el compilador, no algo que el compilador vaya a comprobar.  Si el programa utiliza el modificador declspec `restrict` de manera inapropiada, el programa podrá tener un comportamiento incorrecto.  
  
 Para obtener más información, vea [restrict](../../cpp/restrict.md).  
  
 El modificador declspec `noalias` también se aplica sólo a funciones, e indica que la función es una función semipura.  Una función semipura es aquella que modifica o hace referencia únicamente a variables locales, argumentos y direccionamientos indirectos de primer nivel de argumentos.  Este modificador declspec es una sugerencia para el compilador, y si la función hace referencia a variables globales o direccionamientos indirectos de segundo nivel de argumentos a punteros, el compilador podrá generar código que interrumpa la aplicación.  
  
 Para obtener más información, vea [noalias](../../cpp/noalias.md).  
  
## Directivas pragma de optimización  
 Hay también varias directivas pragma útiles para ayudar a optimizar el código.  La primera que se describirá es `#pragma optimize`:  
  
```  
#pragma optimize("{opt-list}", on | off)  
```  
  
 Esta directiva pragma le permite establecer un nivel de optimización función a función.  Este sistema es perfecto para esas raras ocasiones en las que la aplicación se bloquea cuando una función determinada se compila con optimización.  Puede utilizarlo para desactivar las optimizaciones para una función única:  
  
```  
#pragma optimize("", off)  
int myFunc() {...}  
#pragma optimize("", on)  
```  
  
 Para obtener más información, vea [optimize](../../preprocessor/optimize.md).  
  
 Los procesos en línea son una de las optimizaciones más importantes que ejecuta el compilador y aquí se van a describir un par de directivas pragma que ayudan a modificar este comportamiento.  
  
 `#pragma inline_recursion` es útil para especificar si se desea o no que la aplicación procese en línea una llamada recursiva.  De forma predeterminada está desactivada.  En el caso de recursividad superficial de funciones pequeñas, puede activarla.  Para obtener más información, vea [inline\_recursion](../../preprocessor/inline-recursion.md).  
  
 Otra directiva pragma útil para limitar la profundidad del procesamiento en línea es `#pragma inline_depth`.  Sobre todo resulta útil en aquellas situaciones en las que se intenta limitar el tamaño de un programa o función.  Para obtener más información, vea [inline\_depth](../../preprocessor/inline-depth.md).  
  
## \_\_restrict y \_\_assume  
 Visual C\+\+ incluye un par de palabras clave que pueden mejorar el rendimiento: [\_\_restrict](../../cpp/extension-restrict.md) y [\_\_assume](../../intrinsics/assume.md).  
  
 En primer lugar, se debería tener en cuenta que `__restrict` y `__declspec(restrict)` son diferentes.  Aunque están relacionadas de algún modo, su semántica es diferente.  `__restrict` es un calificador de tipo, como `const` o `volatile`, pero exclusivamente para los tipos de puntero.  
  
 Un puntero que se modifica con `__restrict` se denomina *puntero \_\_restrict*.  Un puntero \_\_restrict es un puntero al que sólo se puede tener acceso a través del puntero \_\_restrict.  En otras palabras, no se puede utilizar otro puntero para tener acceso a los datos señalados por el puntero \_\_restrict.  
  
 `__restrict` puede ser una herramienta eficaz para el optimizador de Visual C\+\+, pero hay que utilizarla con cuidado.  Si se utiliza incorrectamente, el optimizador podría realizar una optimización que interrumpiría su aplicación.  
  
 La palabra clave `__restrict` reemplaza el modificador **\/Oa** de las versiones anteriores.  
  
 Con `__assume,` el desarrollador puede indicar al compilador que haga suposiciones sobre el valor de alguna variable.  
  
 Por ejemplo, `__assume(a < 5);` indica al optimizador que en esa línea de código la variable `a` es menor que 5.  De nuevo, esto es una sugerencia para el compilador.  Si `a` es realmente 6 es en este punto del programa, el comportamiento de este después de que el compilador haya realizado la optimización puede ser distinto de lo que se esperaba.  `__assume` es más útil antes de cambiar instrucciones o expresiones condicionales.  
  
 Hay algunas limitaciones en `__assume`.  En primer lugar, al igual que `__restrict`, es sólo una sugerencia, por lo que el compilador puede omitirlo sin mayor problema.  Además, `__assume` funciona actualmente sólo con desigualdades de variables frente a constantes.  No difunde desigualdades simbólicas, por ejemplo, assume\(a \< b\).  
  
## Compatibilidad intrínseca  
 Las funciones intrínsecas son llamadas a función en las que el compilador tiene un conocimiento intrínseco sobre la llamada, y en lugar de llamar a una función de una biblioteca, emite código para esa función.  El archivo de encabezado intrin.h ubicado en \<directorio\_instalación\>\\VC\\include\\intrin.h contiene todas las funciones intrínsecas disponibles para cada una de las tres plataformas compatibles \(x86, x64 y ARM\).  
  
 Las funciones intrínsecas dan al programador la capacidad para profundizar en el código sin tener que utilizar el ensamblado.  Las funciones intrínsecas presentan varias ventajas:  
  
1.  El código es más portátil.  Algunas de las funciones intrínsecas están disponibles en varias arquitecturas de la CPU.  
  
2.  El código es más fácil de leer, ya que se sigue escribiendo en C\/C\+\+.  
  
3.  El código presenta las ventajas de las optimizaciones del compilador.  A medida que el compilador mejora, también lo hace la generación de código para las funciones intrínsecas.  
  
 Para obtener más información, vea [Intrínsecos del controlador](../../intrinsics/compiler-intrinsics.md) y [Benefits of Using Intrinsics](http://msdn.microsoft.com/es-es/57af8920-527f-44af-a741-a07cbe80bf02).  
  
## Excepciones  
 Hay una merma en el rendimiento asociada al uso de excepciones.  Se introducen algunas restricciones al utilizar bloques Try que impiden que el compilador realice ciertas optimizaciones.  En las plataformas x86 hay una degradación del rendimiento adicional de los bloques Try debido a la información de estado adicional que se debe generar durante la ejecución del código.  En las plataformas de 64 bits, los bloques Try no degradan tanto el rendimiento, pero cuando se produce la excepción, el proceso de encontrar el controlador y desenredar la pila puede ser costoso.  
  
 Por consiguiente, se recomienda evitar la introducción de bloques Try\/Catch en código que no lo necesite realmente.  Si tiene que usar excepciones, utilice si es posible excepciones sincrónicas.  Para obtener más información, vea [Control de excepciones estructurado](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Por último, sólo produzca excepciones para casos excepcionales.  La utilización de excepciones para el flujo de control general probablemente hagan que el rendimiento se resienta.  
  
## Vea también  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)