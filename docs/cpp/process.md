---
title: proceso
ms.date: 11/04/2016
f1_keywords:
- process_cpp
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
ms.openlocfilehash: 049360dddff2b9ca2ea460b96e027e86899f1ecb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344994"
---
# <a name="process"></a>proceso

Especifica que el proceso de la aplicación administrada debe tener una única copia de una variable global determinada, una variable miembro estática o una variable local estática compartida en todos los dominios de aplicación del proceso. Esto se diseñó principalmente para utilizarse cuando se compila con **/CLR: pure**, que está en desuso en Visual Studio 2017 y no admitido en Visual Studio 2017. Cuando se compila con **/CLR**, las variables globales y estáticas son por proceso de forma predeterminada y no es necesario usar **__declspec (proceso)**.

Solo una variable global, una variable miembro estática o una variable local estática de tipo nativo puede marcarse con **__declspec (proceso)**.

**proceso** solo es válido cuando se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Si desea que cada dominio de aplicación tiene su propia copia de una variable global, use [appdomain](../cpp/appdomain.md).

Consulte [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md) para obtener más información.

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
