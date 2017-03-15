---
title: "Consideraciones de rendimiento para la interoperabilidad (C++) | Microsoft Docs"
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
  - "/clr (opción del compilador) [C++], consideraciones de rendimiento para la interoperabilidad"
  - "interoperabilidad [C++], consideraciones sobre rendimiento"
  - "interoperabilidad [C++], consideraciones de rendimiento"
  - "ensamblados mixtos [C++], consideraciones de rendimiento"
  - "invocación de plataforma [C++], interoperabilidad"
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Consideraciones de rendimiento para la interoperabilidad (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema, se proporcionan instrucciones para reducir el efecto de las transiciones por interoperabilidad entre administrado y no administrado en el rendimiento en tiempo de ejecución.  
  
 Visual C\+\+ admite los mismos mecanismos de interoperabilidad que otros lenguajes de .NET, como Visual Basic y C\# \(P\/Invoke\), pero además proporciona compatibilidad para interoperabilidad específica de Visual C\+\+ \(interoperabilidad de C\+\+\).  Para las aplicaciones a las que afecta en gran medida el rendimiento, es importante entender las implicaciones en el rendimiento de cada técnica de interoperabilidad.  
  
 Independientemente de la técnica de interoperabilidad empleada, cada vez que una función administrada llama a una función no administrada o viceversa, se requieren secuencias de transición especiales, llamadas códigos thunk.  El compilador de Visual C\+\+ inserta automáticamente estos códigos thunk, pero es importante tener en cuenta que, acumulativamente, estas transiciones pueden tener un alto costo en el rendimiento.  
  
## Reducir las transiciones  
 Una manera de evitar o reducir el costo de código thunk de interoperabilidad es refactorizar las interfaces implicadas para minimizar las transiciones entre administrado y no administrado.  Se pueden obtener mejoras considerables en el rendimiento estableciendo como destino unas interfaces que impliquen llamadas frecuentes por el límite entre administrado y no administrado.  Una función administrada que llama a una función no administrada en un bucle ajustado, por ejemplo, es una buena candidata para la refactorización.  Si el propio bucle se mueve al lado no administrado, o si se crea una alternativa administrada a la llamada no administrada \(tal vez poniendo en la cola datos del lado administrado y luego calculando sus referencias a la API no administrada, todo simultáneamente después del bucle\), se puede reducir el número de transiciones de manera importante.  
  
## P\/Invoke frente a la interoperabilidad de C\+\+  
 Para los lenguajes de .NET, como Visual Basic y C\#, el método prescrito para interoperar con componentes nativos es P\/Invoke.  Dado que P\/Invoke es compatible con .NET Framework, también lo es con Visual C\+\+, pero Visual C\+\+ proporciona además su propia compatibilidad para interoperabilidad, que se conoce como interoperabilidad de C\+\+.  La interoperabilidad de C\+\+ es preferible a P\/Invoke porque P\/Invoke no posee seguridad de tipos.  Como resultado, los informes de errores se crean principalmente en tiempo de ejecución, pero la interoperabilidad de C\+\+ también tiene ventajas en cuanto al rendimiento respecto a P\/Invoke.  
  
 Ambas técnicas requieren que se den determinadas circunstancias siempre que una función administrada llame a una función no administrada:  
  
-   Se calculan las referencias de los argumentos de llamada a la función desde CLR a tipos nativos.  
  
-   Se ejecuta un código thunk de administrado a no administrado.  
  
-   Se llama a la función no administrada \(utilizando las versiones nativas de los argumentos\).  
  
-   Se ejecuta un código thunk de no administrado a administrado.  
  
-   Se calculan las referencias del tipo de valor devuelto y cualquier argumento "out" o "in,out" desde tipos nativos a CLR.  
  
 Los códigos thunk entre administrado y no administrado son necesarios para que la interoperabilidad funcione, pero el cálculo de referencias de datos que se requiere depende de los tipos de datos implicados, de la firma de la función y de cómo se van a usar los datos.  
  
 El cálculo de referencias de datos efectuado mediante la interoperabilidad de C\+\+ es la forma más sencilla posible: simplemente se copian los parámetros bit a bit a través del límite entre administrado y no administrado; no se efectúa ninguna transformación.  Para P\/Invoke, esto sólo es así si todos los parámetros son simples, de tipos que pueden transferirse en bloque de bits.  De lo contrario, P\/Invoke sigue unos pasos muy eficaces para convertir cada parámetro administrado a un tipo nativo apropiado, y viceversa si los argumentos están marcados como "out", o "in,out".  
  
 Dicho de otro modo, la interoperabilidad de C\+\+ utiliza el método de cálculo de referencias de datos más rápido posible, mientras que P\/Invoke utiliza el método más eficaz.  Esto significa que la interoperabilidad de C\+\+ \(de una forma típica para C\+\+\) proporciona un rendimiento óptimo de forma predeterminada, y el programador es el responsable de tratar los casos en los que este comportamiento no sea seguro o adecuado.  
  
 Por tanto, la interoperabilidad de C\+\+ requiere que el cálculo de referencias de datos se proporcione de manera explícita, pero la ventaja es que el programador es libre de decidir lo que es apropiado, en función de la naturaleza de los datos, y cómo utilizarlos.  Además, aunque el comportamiento del cálculo de referencias de datos con P\/Invoke se puede modificar personalizándose hasta cierto punto, la interoperabilidad de C\+\+ permite personalizar el cálculo de referencias de datos para cada llamada.  Esto no es posible con P\/Invoke.  
  
 Para obtener más información sobre la interoperabilidad de C\+\+, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)