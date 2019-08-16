---
title: Consideraciones de rendimiento para la interoperabilidad (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: 29dbfa6465f6bcbcf4d0618b1820e59a8edbd3a3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447250"
---
# <a name="performance-considerations-for-interop-c"></a>Consideraciones de rendimiento para la interoperabilidad (C++)

Este tema proporciona directrices para reducir el efecto de las transiciones de interoperabilidad administrado y no en el rendimiento de tiempo de ejecución.

Visual C++ admite los mismos mecanismos de interoperabilidad que otros lenguajes. NET, como Visual Basic y C# (P/Invoke), pero también proporciona compatibilidad para interoperabilidad es específica de Visual C++ (interoperabilidad de C++). Para las aplicaciones críticas para el rendimiento, es importante entender las implicaciones de rendimiento de cada técnica de interoperabilidad.

Independientemente de la interoperabilidad técnica empleada, secuencias de transición especial, llamadas fragmentos de código thunk, se requieren cada vez que una función o viceversa no administrada llama a una función administrada. Estos fragmentos de código thunk se insertan automáticamente por Microsoft C++ compilador, pero es importante tener en cuenta que, de manera acumulativa, estas transiciones pueden tener un costosas en términos de rendimiento.

## <a name="reducing-transitions"></a>Reducir las transiciones

Una manera de evitar o reducir el costo de código thunk de interoperabilidad es refactorizar las interfaces implicadas para minimizar las transiciones y no administrado. Tomando unas interfaces que impliquen llamadas frecuentes a través del límite administrado y no se pueden realizar mejoras considerables del rendimiento. Una función administrada que llama a una función no administrada en un bucle ajustado, por ejemplo, es un buen candidato para la refactorización. Si el propio bucle se mueve al lado no administrado, o si una alternativa administrada a la llamada no administrada se crea (quizás cola datos en la parte administrada y serialización a la API no administrada a la vez después del bucle), puede ser el número de transiciones reduce el inicio de sesión ificantly.

## <a name="pinvoke-vs-c-interop"></a>Vs P/Invoke. Interoperabilidad de C++

Para los lenguajes. NET, como Visual Basic y C#, el método prescrito para interoperar con componentes nativos es P/Invoke. Dado que P/Invoke es compatible con .NET Framework, Visual C++ admite también, pero Visual C++ también proporciona su propia compatibilidad para interoperabilidad, que se conoce como la interoperabilidad de C++. Interoperabilidad de C++ es preferible a través de P/Invoke porque P/Invoke no tiene seguridad de tipos. Como resultado, los errores se notifican principalmente en tiempo de ejecución, pero la interoperabilidad de C++ también tiene ventajas de rendimiento a través de P/Invoke.

Ambas técnicas requieren varios aspectos que ocurre cada vez que una función administrada llama a una función no administrada:

- Los argumentos de llamada de función se calculan las referencias de CLR a tipos nativos.

- Se ejecuta un código thunk a administrado.

- Se llama a la función no administrada (utilizando las versiones nativas de los argumentos).

- Se ejecuta un código thunk no administrado a administrado.

- El tipo de valor devuelto y los "out" o "en, out" argumentos se calculan las referencias de código nativo a tipos CLR.

El código thunk administrado y no es necesario para la interoperabilidad funcione en absoluto, pero el cálculo de referencias de datos que es necesario depende de los tipos de datos implicados, la firma de función y uso de los datos.

El cálculo de referencias de datos realizadas por la interoperabilidad de C++ es la forma más sencilla posible: simplemente se copian los parámetros a través del límite de una manera de bit a bit; y no administrado se realiza ninguna transformación en absoluto. Para P/Invoke, esto solo es true si todos los parámetros son simples, tipos de bits/bytes. En caso contrario, P/Invoke realiza pasos muy eficaces para convertir cada parámetro administrado a un tipo nativo apropiado, y viceversa, si los argumentos están marcados como "out", o "en, out".

En otras palabras, interoperabilidad de C++ utiliza el método más rápido posible de serialización de datos, mientras que P/Invoke utiliza el método más eficaz. Esto significa que la interoperabilidad de C++ (de una manera típica de C++) proporciona un rendimiento óptimo de forma predeterminada, y el programador es responsable de tratar los casos donde este comportamiento no es seguro o adecuado.

Por lo tanto, la interoperabilidad de C++ requiere que el cálculo de referencias debe proporcionarse explícitamente, pero la ventaja es que el programador es libre de decidir lo que sea adecuado, dada la naturaleza de los datos y cómo es que se usará. Además, aunque puede modificar el comportamiento de serialización de datos de P/Invoke en Personalizar hasta cierto punto, interoperabilidad de C++ permite la serialización para personalizarse en llamada por otra base de datos. Esto no es posible con P/Invoke.

Para obtener más información acerca de la interoperabilidad de C++, vea [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
