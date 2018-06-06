---
title: Comparación de características mixta, pura y comprobable (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- safe assemblies [C++], vs. pure
- mixed assemblies [C++], vs. pure
- safe assemblies [C++], vs. mixed
- pure MSIL [C++]
- verifiable assemblies [C++]
- pure MSIL [C++], vs. safe
- pure MSIL [C++], vs. mixed
- pure MSIL [C++], compared to mixed and safe
- verifiable assemblies [C++], vs. mixed
- mixed assemblies [C++], vs. safe
- verifiable assemblies [C++], vs. pure
- pure assemblies [C++]
- safe assemblies [C++]
- mixed assemblies [C++]
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cb1b2ba71277415fd1ba5124f6120cc2f2c995d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704716"
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Comparación de características mixta, pura y comprobable (C++ / CLI)

Este tema comparan las características entre los distintos **/CLR** modos de compilación. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

> [!IMPORTANT]
> El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

## <a name="feature-comparison"></a>Comparación de características

|Característica|Mixta (/clr)|Pura (/clr:pure)|Seguro (/ CLR: safe)|Información relacionada|
|-------------|---------------------|-------------------------|-------------------------|-------------------------|
|Biblioteca de CRT|Admite|en desuso||[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)|
|MFC/ATL|Admite|||[Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md) &#124; [información general de clases](../atl/atl-class-overview.md)|
|Funciones no administradas|Admite|||[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)|
|Datos no administrados|Admite|en desuso||[Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|
|Puede llamar desde funciones no administradas|Admite||||
|Admite llamadas a funciones no administradas|Admite|en desuso|en desuso|[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|
|Admite la reflexión|Sólo archivos DLL|en desuso|en desuso|[Reflexión (C++-CLI)](../dotnet/reflection-cpp-cli.md)|

## <a name="see-also"></a>Vea también

- [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)