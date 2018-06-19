---
title: Consideraciones de rendimiento para la interoperabilidad (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9223c52e4ef831a9a1ff657db1a0d7859dd6ce6c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164055"
---
# <a name="performance-considerations-for-interop-c"></a>Consideraciones de rendimiento para la interoperabilidad (C++)
Este tema proporciona directrices para reducir el efecto de las transiciones de interoperabilidad administrado y en el rendimiento de tiempo de ejecución.  
  
 Visual C++ admite los mismos mecanismos de interoperabilidad que otros lenguajes. NET, como Visual Basic y C# (P/Invoke), pero también proporciona la capacidad de interoperabilidad que es específica de Visual C++ (interoperabilidad de C++). Para las aplicaciones críticas para el rendimiento, es importante entender las implicaciones de rendimiento de cada técnica de interoperabilidad.  
  
 Independientemente de la técnica de interoperabilidad empleada, secuencias de transición especiales, llamadas códigos thunk, se requieren cada vez que una función administrada llama a una función o viceversa no administrada. Estos fragmentos de código thunk se insertan automáticamente por el compilador de Visual C++, pero es importante tener en cuenta que, acumulativamente, estas transiciones pueden tener un costosas en términos de rendimiento.  
  
## <a name="reducing-transitions"></a>Reducir las transiciones  
 Una manera de evitar o reducir el costo de thunks de interoperabilidad es refactorizar las interfaces implicadas para minimizar las transiciones y no administrado. Considerablemente el rendimiento se puede mejorar mediante la orientación de las interfaces locuaces, que son aquellos que impliquen llamadas frecuentes a través del límite administrado y no administrado. Una función administrada que llama a una función no administrada en un bucle ajustado, por ejemplo, es una buena candidata para la refactorización. Si el propio bucle se mueve a la parte no administrada, o si una alternativa administrada a la llamada no administrada se crea (quizás cola datos en la parte administrada y, a continuación, serialización a la API no administrada a la vez después del bucle), puede ser el número de transiciones reduce el inicio de sesión ificantly.  
  
## <a name="pinvoke-vs-c-interop"></a>Frente a P/Invoke. Interoperabilidad de C++  
 Para los lenguajes. NET, como Visual Basic y C#, el método prescrito para interoperar con componentes nativos es P/Invoke. Dado que P/Invoke es compatible con .NET Framework, Visual C++ admite también, pero Visual C++ también proporciona su propia compatibilidad para interoperabilidad, que se denomina interoperabilidad de C++. Interoperabilidad de C++ es preferible a través de P/Invoke porque P/Invoke no tiene seguridad de tipos. Como resultado, los errores se notifican principalmente en tiempo de ejecución, pero la interoperabilidad de C++ también tiene ventajas de rendimiento a través de P/Invoke.  
  
 Ambas técnicas requieren varios aspectos que se produzca cada vez que una función administrada llama a una función no administrada:  
  
-   Los argumentos de llamada de función se serializan de CLR a tipos nativos.  
  
-   Se ejecuta un código thunk a administrado.  
  
-   Se llama a la función no administrada (utilizando las versiones nativas de los argumentos).  
  
-   Se ejecuta un código thunk de no administrado a administrado.  
  
-   El tipo de valor devuelto y los "out" o "en, out" se calculan las referencias de los argumentos de código nativo a tipos CLR.  
  
 Los fragmentos de código thunk administrado y no son necesarios para la interoperabilidad a funcionará en absoluto, pero el cálculo de referencias de datos que se requiere depende de los tipos de datos implicados, la firma de función y cómo se utilizarán los datos.  
  
 El cálculo de referencias de datos realizadas por la interoperabilidad de C++ es la forma más sencilla posible: simplemente se copian los parámetros a través del límite administrado y no administrado de forma bit a bit; no se realiza ninguna transformación en absoluto. Para P/Invoke, esto es cierto solo si todos los parámetros son simples, tipos de bits/bytes. De lo contrario, P/Invoke realiza unos pasos muy eficaces para convertir cada parámetro administrado a un tipo nativo apropiado, y viceversa si los argumentos están marcados como "out" o "en, out".  
  
 En otras palabras, la interoperabilidad de C++ utiliza el método más rápido posible de la serialización de datos, mientras que P/Invoke utiliza el método más eficaz. Esto significa que la interoperabilidad de C++ (de forma habitual de C++) proporciona un rendimiento óptimo de forma predeterminada, y el programador es responsable de tratar los casos donde este comportamiento no sea seguro o adecuado.  
  
 Por tanto, la interoperabilidad de C++ requiere que la serialización de datos debe proporcionarse explícitamente, pero la ventaja es que el programador es libre de decidir qué es más apropiado, dada la naturaleza de los datos y cómo va a usarse. Además, aunque puede modificar el comportamiento de serialización de datos de P/Invoke en Personalizar hasta cierto punto, la interoperabilidad de C++ permite el cálculo de referencias para que se pueden personalizar en llamada por otra base de datos. Esto no es posible con P/Invoke.  
  
 Para obtener más información sobre la interoperabilidad de C++, vea [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)