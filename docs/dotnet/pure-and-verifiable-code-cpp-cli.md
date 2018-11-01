---
title: Código puro y comprobable (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
ms.openlocfilehash: 11cccc082d5b9e467f5fafce6f2128aa50d33879
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512826"
---
# <a name="pure-and-verifiable-code-ccli"></a>Código puro y comprobable (C++ / c++ / CLI)

Para la programación. NET, Visual C++ en Visual Studio 2017 admite la creación de ensamblados mixtos mediante la [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador. El **/CLR: pure** y **CLR: safe** opciones están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017. Si el código debe ser seguro o que se pueda comprobar, se recomienda trasladarlo a C#.

## <a name="mixed-clr"></a>Mixta (/clr)

Ensamblados mixtos (compilados con **/CLR**), contienen no administrados y las partes administradas, lo que permite usar características. NET, pero siguen contengan código nativo. Esto permite actualizar aplicaciones y componentes para utilizar las características de .NET sin tener que volver a escribir el proyecto completo. Uso de Visual C++ para mezclar código administrado y nativo de este modo se denomina interoperabilidad de C++. Para obtener más información, consulte [ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md) y [nativo e interoperabilidad de .NET](../dotnet/native-and-dotnet-interoperability.md).

Las llamadas realizadas desde ensamblados administrados a archivos DLL nativos a través de P/Invoke se compilarán, pero pueden producir un error en tiempo de ejecución según la configuración de seguridad.

Existe un escenario de codificación que cumplirá los requisitos del compilador, pero que dará como resultado un ensamblado no comprobable: llamar a una función virtual a través de una instancia de objeto mediante un operador de resolución de ámbito.  Por ejemplo: `MyObj -> A::VirtualFunction();`.

## <a name="see-also"></a>Vea también

- [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

