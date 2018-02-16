---
title: "Código puro y comprobable (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ba218772bdedf772e995bb9289b18452d599e6c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="pure-and-verifiable-code-ccli"></a>Código puro y comprobable (C++/CLI)
Para la programación. NET, Visual C++ en Visual Studio de 2017 admite la creación de ensamblados mixtos mediante la [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) opción del compilador. El **/CLR: pure** y **CLR: safe** opciones han quedado en desuso a partir de Visual Studio 2015 y se quitará en una versión futura del compilador. Si el código debe ser comprobable, se recomienda que se traslade a C#.
  
## <a name="mixed-clr"></a>Mixta (/clr)  
 Ensamblados mixtos (compilados con **/CLR**), contienen no administrado y partes administradas, lo que les permite utilizar características. NET, pero siguen contengan código nativo. Esto permite actualizar aplicaciones y componentes para utilizar las características de .NET sin tener que volver a escribir el proyecto completo. El uso de Visual C++ para mezclar código administrado y nativo de este modo se denomina interoperabilidad de C++. Para obtener más información, consulte [ensamblados mixto (nativo y administrado)](../dotnet/mixed-native-and-managed-assemblies.md) y [nativo y la interoperabilidad de .NET](../dotnet/native-and-dotnet-interoperability.md).  
  
  
Llamadas realizadas desde ensamblados administrados a archivos DLL nativos a través de P/Invoke se compilarán, pero pueden producir un error en tiempo de ejecución según la configuración de seguridad.  
  
Existe un escenario de codificación que cumplirá los requisitos del compilador, pero que dará como resultado un ensamblado no comprobable: llamar a una función virtual a través de una instancia de objeto mediante un operador de resolución de ámbito.  Por ejemplo: `MyObj -> A::VirtualFunction();`.  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
