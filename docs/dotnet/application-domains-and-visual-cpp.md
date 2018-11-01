---
title: Dominios de aplicación y Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 2296654e6935bc40f301226b184cf34f77cb126d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539274"
---
# <a name="application-domains-and-visual-c"></a>Dominios de aplicación y Visual C++

Si tiene un `__clrcall` función virtual, que será la vtable por dominio de aplicación (appdomain). Si crea un objeto en un appdomain, sólo puede llamar a la función virtual desde dentro de ese appdomain. En modo mixto (**/CLR**) tendrá vtables por proceso si el tipo no tiene ningún `__clrcall` funciones virtuales. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Para obtener más información, consulte:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Vea también

- [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)