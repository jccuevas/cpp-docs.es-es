---
title: "Problemas comunes de migraci&#243;n de ARM en Visual C++ | Microsoft Docs"
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
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Problemas comunes de migraci&#243;n de ARM en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El mismo código fuente de Visual C\+\+ podría generar resultados diferentes en la arquitectura de ARM que en x86 o arquitecturas x64.  
  
## Orígenes de los problemas de migración  
 Muchos problemas que pueden surgir al migrar código x86 o arquitecturas x64 a la arquitectura de ARM se relacionan con las construcciones de código fuente que pueden invocar un comportamiento no definido, implementación\- definido, o sin especificar.  
  
 Un comportamiento no definido  
 Comportamiento del estándar de C\+\+ no define y, que es provocado por una operación que no tenga razonable resultado\- para el ejemplo, la conversión de un valor flotante en un entero sin signo, o moverse un valor por varias posiciones que es negativo o supera el número de bits del tipo se promueve.  
  
 Comportamiento Implementación\-definido  
 Comportamiento del estándar de C\+\+ requiere el proveedor de compilador defina y el documento.  Un programa puede confiar en comportamiento implementación\- definido, aunque el hacerlo no sea portable.  Los ejemplos de comportamiento implementación\- definido incluyen los tamaños de tipos integrados y sus requisitos de alineación.  Un ejemplo de una operación que podría afectar al comportamiento implementación\- definido está teniendo acceso a la lista de argumentos de variable.  
  
 Comportamiento sin especificar  
 Comportamiento de que el estándar de C\+\+ sale deliberadamente no determinista.  Aunque el comportamiento se considere no determinista, las invocaciones desde el comportamiento sin especificar vienen determinadas por la implementación del compilador.  Sin embargo, no hay ningún requisito para que un proveedor del compilador predetermine el resultado o garantiza un comportamiento coherente entre llamadas comparables, y no hay ningún requisito de la documentación.  Un ejemplo de un comportamiento no especificado es el orden en el que sub\-expresión\- que incluyen los argumentos de una función llamada\- se evalúan.  
  
 Otros problemas de migración se puede atribuir a las diferencias de hardware entre la ARM y x86 o arquitecturas x64 que interactúan con el estándar de C\+\+ de manera diferente.  Por ejemplo, el modelo de memoria seguros x86 y arquitectura x64 da `volatile`\- variables calificadas algunas propiedades adicionales que se han utilizado para facilitar algunas clases de comunicación de inter\- subproceso en el pasado.  Pero el modelo de memoria débil de la arquitectura de ARM no admite este uso, ni el estándar de C\+\+ lo requiere.  
  
> [!IMPORTANT]
>  Aunque `volatile` gane algunas propiedades que se pueden utilizar para implementar formularios limitados de comunicación de inter\- subproceso en x86 y x64, estas propiedades adicionales no son suficientes para implementar la comunicación de inter\- subproceso en general.  El estándar de C\+\+ recomienda esta comunicación se implementa mediante primitivas de sincronización apropiados en su lugar.  
  
 Porque las distintas plataformas pueden expresar estas clases de comportamiento de manera diferente, trasladar el software entre plataformas puede ser difícil y error\- susceptible si depende del comportamiento de una plataforma específica.  Aunque muchas de estas clases de comportamiento se puede observar y pueden aparecer estables, confianza en ellas por lo menos no portátil y, cuando se trata de un comportamiento indefinido o sin especificar, también es un error.  Aunque el comportamiento que se cita en este documento no se debe confiar en, y podría cambiar en los compiladores futuros o implementaciones de CPU.  
  
## Problemas de migración de ejemplo  
 El resto de este documento se describe cómo el comportamiento diferente de estos elementos del lenguaje C\+\+ puede producir resultados diferentes en distintas plataformas.  
  
### Conversión de Flotante\- punto en un entero sin signo  
 En la arquitectura de ARM, la conversión de un valor de punto flotante a un entero de 32 bits satura el valor más próximo que integer puede representar si el valor de punto flotante está fuera del intervalo que integer puede representar.  En arquitecturas x86 y x64, los ajustes de la conversión a si el entero es sin signo, o se establecen en \-2147483648 si se firma integer.  Ninguna de estas arquitecturas admiten directamente la conversión de valores de punto flotante a tipos enteros menores; en su lugar, las conversiones se realizan a 32 bits, y los resultados se truncan a un tamaño menor.  
  
 Para la arquitectura de ARM, la combinación de saturación y de truncamiento significa que la conversión a tipos sin signo correctamente satura tipos sin signo más pequeños cuando satura un entero de 32 bits, pero genera un resultado truncado por valores que sean mayores que el tipo más pequeño puede representar pero demasiado pequeño para saturar el entero de 32 bits completo.  La conversión también satura correctamente para los enteros con signo de 32 bits, pero el truncamiento de enteros saturados, firmado da lugar a \-1 por valores positivo\- saturados y 0 por valores negativo\- saturados.  La conversión en un entero menor genera un resultado truncado que sea imprevisible.  
  
 Para arquitecturas x86 y x64, la combinación de comportamiento envuelto para las conversiones de entero sin signo y evaluación explícita para las conversiones de tipo entero con signo de desbordamiento, así como el truncamiento, crea los resultados para la mayoría de los cambios imprevistos si son demasiado grandes.  
  
 Estas plataformas también difieren en cómo se controlan la conversión NaN \(No\-uno\- número\) a los tipos enteros.  En la ARM, NaN convierte a 0x00000000; en x86 y x64, convierte a 0x80000000.  
  
 La conversión flotante podría ser de confianza sólo en si sabe que el valor se encuentra dentro del intervalo del tipo entero que se va a convertir.  
  
### Comportamiento del operador de cambio \(\<\< \>\>\)  
 En la arquitectura de ARM, un valor se puede desplazarse a la izquierda o hasta que 255 bits antes de que el modelo comienza a repetir.  En x86 y arquitecturas x64, repite el modelo en cada múltiplo de 32 a menos que el origen del modelo es una variable de 64 bits; en ese caso, el modelo se repite en cada múltiplo de 64 en x64, y cada múltiplo de 256 en x86, donde se usan una implementación de software.  Por ejemplo, para una variable de 32 bits que tiene un valor de 1 cambió a la izquierda por 32 posiciones, en la ARM el resultado es 0, en x86 el resultado es 1, y en x64 el resultado también es 1.  Sin embargo, si el origen del valor es una variable de 64 bits, el resultado en las tres plataformas es 4294967296, y el valor “no se ajustará alrededor” hasta que haya movido 64 posiciones respecto a x64, o 256 posiciones respecto a la ARM y en x86.  
  
 Puesto que el resultado de una operación de cambio que supera el número de bits del tipo de origen es indefinido, el compilador no se requiere tener un comportamiento coherente en todas las situaciones.  Por ejemplo, si ambos operandos de un cambio se conocen en tiempo de compilación, el compilador puede optimizar el programa mediante una rutina interna al calcula previamente el resultado del desplazamiento y después de sustituir el resultado en lugar de la operación de cambio.  Si la cantidad de cambio es demasiado grande, o negativo, el resultado de la rutina interna podría ser diferente del resultado de la misma expresión de cambio que ejecutar por CPU.  
  
### Comportamiento variable de los argumentos \(varargs\)  
 En la arquitectura de ARM, los parámetros de la lista de argumentos de variable que se pasan en la pila se bajo la alineación.  Por ejemplo, un parámetro 64 bits se alinea en un límite de 64 bits.  En x86 y x64, los argumentos que se pasan a la pila no están sujetos a la alineación y no se empaquetan estrechamente.  Esta diferencia puede producir una función variadic como `printf` las direcciones de memoria de lectura que se previstas como relleno en la ARM si no coincide el diseño previsto de la lista de argumentos de variable exactamente, aunque se funciona para un subconjunto de algunos valores en arquitecturas x86 o x64.  Considere este ejemplo:  
  
```  
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.  
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.  
// on ARM the calling convention will align the 64-bit value and the code will print a random value  
printf("%d\n", 1LL);  
  
```  
  
 En este caso, el error se puede corregir asegurándose de que la especificación correcta de formato se utiliza para ver que la alineación del argumento.  Este código es correcto:  
  
```  
// CORRECT: use %I64d for 64-bit integers  
printf("%I64d\n", 1LL);  
  
```  
  
### Orden de evaluación del argumento  
 Porque la ARM, x86, y procesadores x64 es tan diferentes, pueden aparecer diferentes requisitos a las implementaciones del compilador, y también distintas ocasiones para las optimizaciones.  Debido a esto, así como otros factores guste de la convención de llamada y de optimización, un compilador podría evaluar argumentos de función en un orden diferente en arquitecturas diferentes o cuando se cambian los otros factores.  Esto puede provocar un comportamiento de una aplicación que se base en un orden concreto de evaluación de cambiar inesperado.  
  
 Esta clase de error puede aparecer cuando los argumentos de una función tienen efectos secundarios que impacten otros argumentos a la función de llamada.  Esta clase de dependencia normalmente es fácil de evitar, pero puede ser obscurecida a veces por las dependencias que son difíciles de discernir, o por la sobrecarga de operadores.  Considere este ejemplo de código:  
  
```  
handle memory_handle;  
  
memory_handle->acquire(*p);  
  
```  
  
 Se produce bien definido, pero si `->` y `*` son operadores sobrecargados, este código se traduce algo similar a este:  
  
```  
Handle::acquire(operator->(memory_handle), operator*(p));  
```  
  
 Y si hay una dependencia entre `operator->(memory_handle)` y `operator*(p)`, el código podría basarse en un orden concreto de evaluación, aunque el código original parece que no hay ninguna dependencia posible.  
  
### comportamiento predeterminado volatile de la palabra clave  
 El compilador de Microsoft C\+\+ admite dos diferentes interpretaciones de calificador de almacén volátil que puede especificar mediante el compilador.  El modificador **\/volatile:ms** selecciona Microsoft extendidas semántica volátil que garantiza el orden seguro, como ha recibido el caso tradicional para x86 y x64 en el compilador de Microsoft debido al modelo de memoria seguros en las arquitecturas.  El modificador **\/volatile:iso** selecciona la semántica volatile estándar estricta de C\+\+ que no garantiza el orden segura.  
  
 En la arquitectura de ARM, el valor predeterminado es **\/volatile:iso** porque los procesadores de ARM tienen un modelo de memoria débil petición, y porque tenía que el software de ARM no tiene una herencia de confianza en la semántica extendida de **\/volatile:ms** y no hace normalmente interfaz con el software que lo hace.  Sin embargo, sigue siendo a veces adecuado o incluso necesarios para compilar un programa de armamento para utilizar semántica extendida.  Por ejemplo, puede ser demasiado costosos al puerto al programa usar la semántica de ISO C\+\+, o el software del controlador podría observar la semántica tradicional para funcionar correctamente.  En estos casos, puede utilizar el modificador **\/volatile:ms**; sin embargo, para volver a crear la semántica volatile tradicional en destinos de ARM, debe insertar barreras de memoria alrededor de cada lectura o escritura de una variable de `volatile` para aplicar el orden seguros, que puede tener un impacto negativo en el rendimiento.  
  
 En arquitecturas x86 y x64, el valor predeterminado es **\/volatile:ms** porque gran parte del software que se ha creado para estas arquitecturas mediante el compilador de Microsoft C\+\+ se basa en ellas.  Al compilar x86 y programas x64, especifique el modificador **\/volatile:iso** para ayudar a evitar confianza innecesaria en la semántica volatile tradicional, y a promover portabilidad.  
  
## Vea también  
 [Configurar programas para procesadores ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)