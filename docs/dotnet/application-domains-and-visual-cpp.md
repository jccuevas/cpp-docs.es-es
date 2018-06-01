---
title: Dominios de aplicación y Visual C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b935b9a5d1561fa1c8b961ee48b92f59b98e2bd2
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704339"
---
# <a name="application-domains-and-visual-c"></a>Dominios de aplicación y Visual C++

Si tiene un `__clrcall` función virtual, que será la vtable por dominio de aplicación (appdomain). Si crea un objeto en un appdomain, solo puede llamar a la función virtual desde dentro de ese appdomain. En modo mixto (**/CLR**) tendrá tablas virtuales por proceso si el tipo no tiene ningún `__clrcall` funciones virtuales. El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Para obtener más información, consulte:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [process](../cpp/process.md)

## <a name="see-also"></a>Vea también

- [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)