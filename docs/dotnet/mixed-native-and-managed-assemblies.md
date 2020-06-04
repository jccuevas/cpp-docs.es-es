---
title: Ensamblados mixtos (nativos y administrados)
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544511"
---
# <a name="mixed-native-and-managed-assemblies"></a>Ensamblados mixtos (nativos y administrados)

Los ensamblados mixtos son capaces de contener tanto instrucciones máquina no administradas como instrucciones MSIL. Esto les permite llamar a los componentes de .NET y llamarlos, a la vez que conservan la compatibilidad con las bibliotecas nativas C++ . Mediante el uso de ensamblados mixtos, los desarrolladores pueden crear aplicaciones con C++ una combinación de .net y código nativo.

Por ejemplo, una biblioteca existente que consta únicamente de código C++ nativo se puede enviar a la plataforma .net volviendo a compilar un solo módulo con el modificador de compilador **/CLR** . Este módulo puede utilizar las características de .NET pero sigue siendo compatible con el resto de la aplicación. Incluso es posible decidir entre compilaciones nativas y administradas en función de cada función dentro del mismo archivo (vea [administrado, no administrado](../preprocessor/managed-unmanaged.md)).

Visual C++ solo admite la generación de ensamblados administrados mixtos mediante la opción del compilador **/CLR** . Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017. Si necesita ensamblados administrados puros o comprobables, le recomendamos que C#los cree mediante el uso de.

Las versiones anteriores del conjunto C++ de herramientas del compilador de Microsoft admitían la generación de tres tipos distintos de ensamblados administrados: mixto, puro y comprobable. Los dos últimos se tratan en [código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>En esta sección

[Cómo: migrar a/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Describe los pasos recomendados para introducir o actualizar la funcionalidad de .NET en la aplicación.

[Cómo: compilar código de MFC y ATL mediante/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Explica cómo compilar los programas MFC y ATL existentes para usarlos en Common Language Runtime.

[Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Describe el problema del "bloqueo del cargador" y soluciones.

[Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Describe cómo usar las bibliotecas nativas en las compilaciones de **/CLR** .

[Consideraciones de rendimiento](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Describe las implicaciones de rendimiento de los ensamblados mixtos y la serialización de datos.

[Dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Explica la compatibilidad de Visual C++ para dominios de aplicación.

[Doble thunk](../dotnet/double-thunking-cpp.md)<br/>
Trata de las implicaciones de rendimiento de un punto de entrada nativo para una función administrada.

[Evitar excepciones al apagar CLR cuando se usan objetos COM compilados con/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Describe cómo garantizar el cierre correcto de una aplicación administrada que consume un objeto COM compilado con **/CLR**.

[Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Describe cómo crear una aplicación de Common Language Runtime de confianza parcial mediante Visual C++ quitando la dependencia de msvcm90. dll.

Para obtener más información sobre las directrices de codificación de ensamblados mixtos, vea el artículo de MSDN [información general sobre la interoperabilidad de código administrado y no administrado](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Consulte también

- [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)
