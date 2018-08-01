---
title: proceso | Microsoft Docs
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
ms.openlocfilehash: fdad177231c02d2e6f6fad171ae1811ecb9ccc6c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407187"
---
# <a name="process"></a>proceso

Especifica que el proceso de la aplicación administrada debe tener una única copia de una variable global determinada, una variable miembro estática o una variable local estática compartida en todos los dominios de aplicación del proceso. Esto se diseñó principalmente para utilizarse cuando se compila con **/CLR: pure**, que está en desuso en Visual Studio 2017 y no admitido en Visual Studio 2017. Cuando se compila con **/CLR**, las variables globales y estáticas son por proceso de forma predeterminada y no es necesario usar **__declspec (proceso)**.

Solo una variable global, una variable miembro estática o una variable local estática de tipo nativo puede marcarse con **__declspec (proceso)**.

**proceso** solo es válido cuando se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

Si desea que cada dominio de aplicación tiene su propia copia de una variable global, use [appdomain](../cpp/appdomain.md).

Consulte [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md) para obtener más información.

## <a name="see-also"></a>Vea también
 [__declspec](../cpp/declspec.md)  
 [Palabras clave](../cpp/keywords-cpp.md)
