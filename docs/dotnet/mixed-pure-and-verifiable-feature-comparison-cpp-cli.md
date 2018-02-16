---
title: "Comparación de características mixta, pura y comprobable (C++ / CLI) | Documentos de Microsoft"
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ac5e094dd252ec908f352bcc1b19c923513debfb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Comparación de características mixta, pura y comprobable (C++/CLI)
Este tema comparan las características entre los distintos **/CLR** modos de compilación. Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
## <a name="feature-comparison"></a>Comparación de características  
  
|Característica|Mixta (/clr)|Pura (/clr:pure)|Seguro (/ CLR: safe)|Información relacionada|  
|-------------|---------------------|-------------------------|-------------------------|-------------------------|  
|Biblioteca de CRT|Admite|en desuso||[Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC/ATL|Admite|||[Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md) &#124; [Información general de clases](../atl/atl-class-overview.md)|  
|Funciones no administradas|Admite|||[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)|  
|Datos no administrados|Admite|en desuso||[Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|Puede llamar desde funciones no administradas|Admite||||  
|Admite llamadas a funciones no administradas|Admite|en desuso|en desuso|[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|Admite la reflexión|Sólo archivos DLL|en desuso|en desuso|[Reflexión (C++-CLI)](../dotnet/reflection-cpp-cli.md)|  
  
## <a name="see-also"></a>Vea también  
 [Código puro y comprobable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)