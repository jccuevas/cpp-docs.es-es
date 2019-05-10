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
ms.openlocfilehash: 043390a2ebefcadac300b7fb0b05ae7f5ed411f3
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447285"
---
# <a name="mixed-native-and-managed-assemblies"></a>Ensamblados mixtos (nativos y administrados)

Los ensamblados mixtos son capaces de contener tanto instrucciones máquina no administradas como instrucciones MSIL. Esto les permite llamar y ser llamados por componentes. NET, conservando la compatibilidad con bibliotecas de C++ nativas. Mediante ensamblados mixtos, los desarrolladores pueden crear aplicaciones con una mezcla de .NET y el código C++ nativo.

Por ejemplo, una biblioteca existente que consta únicamente de código C++ nativo se puede poner a la plataforma .NET volviendo a compilar sólo un módulo con el **/CLR** modificador del compilador. Este módulo puede utilizar las características de .NET pero sigue siendo compatible con el resto de la aplicación. Incluso es posible decidir entre compilación administrada y nativa según una función por función dentro del mismo archivo (consulte [managed, unmanaged](../preprocessor/managed-unmanaged.md)).

Visual C++ solo admite la generación de ensamblados administrados mixtos mediante la **/CLR** opción del compilador. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017. Si necesita puros o que se pueda comprobar los ensamblados administrados, se recomienda que crearlas en C#.

Las versiones anteriores de Microsoft C++ conjunto de herramientas del compilador admite la generación de tres tipos distintos de ensamblados administrados: mixto, puro y comprobable. Los dos últimos se explican en [código puro y comprobable (C++ / c++ / CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>En esta sección

[Cómo: Migrar a/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Describe los pasos recomendados para introducir o actualizar la funcionalidad de .NET en la aplicación.

[Cómo: Compilar código By Using ATL y MFC/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Explica cómo compilar los programas MFC y ATL existentes para usarlos en Common Language Runtime.

[Inicialización de ensamblados mixtos](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Describe el problema del "bloqueo del cargador" y soluciones.

[Compatibilidad con bibliotecas para ensamblados mixtos](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Describe cómo usar las bibliotecas nativas en **/CLR** compilaciones.

[Consideraciones sobre el rendimiento](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Describe las implicaciones de rendimiento de los ensamblados mixtos y la serialización de datos.

[Dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Explica la compatibilidad de Visual C++ para dominios de aplicación.

[Doble thunk](../dotnet/double-thunking-cpp.md)<br/>
Trata de las implicaciones de rendimiento de un punto de entrada nativo para una función administrada.

[Evitar excepciones CLR apagado cuando se utilizan objetos COM compilados con/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Describe cómo garantizar un apagado correcto de una aplicación administrada que utiliza un objeto COM compilado con **/CLR**.

[Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Describe cómo crear una aplicación de Common Language Runtime de confianza parcial mediante Visual C++, quitando la dependencia de msvcm90.dll.

Para obtener más información sobre cómo codificar instrucciones para ensamblados mixtos, vea el artículo de MSDN [An Overview of administrado y código Interoperability](https://msdn.microsoft.com/library/ms973872.aspx).

## <a name="see-also"></a>Vea también

- [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)
