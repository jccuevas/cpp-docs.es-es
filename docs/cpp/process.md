---
title: proceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b36ec42447aa076d0623707951f82b7b9c95d563
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704911"
---
# <a name="process"></a>proceso

Especifica que el proceso de la aplicación administrada debe tener una única copia de una variable global determinada, una variable miembro estática o una variable local estática compartida en todos los dominios de aplicación del proceso. Esto principalmente estaba destinado a usarse cuando se compila con **/CLR: pure**, que está en desuso en Visual Studio de 2017 y no se admiten en Visual Studio de 2017. Cuando se compila con **/CLR**, variables globales y estáticas son por proceso de forma predeterminada y no es necesario usar `__declspec(process)`.

Solo una variable global, una variable miembro estática o una variable local estática de tipo nativo se pueden marcar con `__declspec(process)`.

`process` solo es válido cuando se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Si desea que cada dominio de aplicación tiene su propia copia de una variable global, utilice [appdomain](../cpp/appdomain.md).

Vea [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md) para obtener más información.

## <a name="see-also"></a>Vea también

- [__declspec](../cpp/declspec.md)
- [Palabras clave](../cpp/keywords-cpp.md)
