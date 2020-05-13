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
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208813"
---
# <a name="application-domains-and-visual-c"></a>Dominios de aplicación y Visual C++

Si tiene una función virtual `__clrcall`, el vtable será por dominio de aplicación (AppDomain). Si crea un objeto en un AppDomain, solo puede llamar a la función virtual desde dentro de ese AppDomain. En modo mixto ( **/CLR**) tendrá vtables por proceso si el tipo no tiene `__clrcall` funciones virtuales. Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

Para más información, consulte:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Consulte también

- [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
