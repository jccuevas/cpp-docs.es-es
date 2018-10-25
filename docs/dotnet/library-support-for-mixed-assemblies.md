---
title: Compatibilidad con bibliotecas para ensamblados mixtos | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8c3fec26f3e41c3edd2346ac2e1b9b1f6b98ba33
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069625"
---
# <a name="library-support-for-mixed-assemblies"></a>Compatibilidad con bibliotecas para ensamblados mixtos

Visual C++ admite el uso de la biblioteca estándar de C++, la biblioteca en tiempo de ejecución de C (CRT), ATL y MFC para aplicaciones compiladas con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md). Esto permite que las aplicaciones existentes que usan estas bibliotecas para usar características de .NET Framework también.

> [!IMPORTANT]
> El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Esta compatibilidad incluye las siguientes bibliotecas DLL y de importación:

- Msvcmrt [d] .lib si se compila con **/CLR**. Ensamblados mixtos vínculo a la biblioteca de importación.

Esta compatibilidad proporciona que algunas ventajas relacionadas:

- La biblioteca estándar de C++ y CRT están disponibles para código mixto. El CRT y la biblioteca estándar de C++ proporcionadas no son comprobables; en última instancia, las llamadas se seguirán enrutando a las mismas CRT y la biblioteca estándar de C++ cuando se utilice desde el código nativo.

- Se corrige el control de excepciones unificado en imágenes mixtas.

- Inicialización estática de variables de C++ en imágenes mixtas.

- Compatibilidad con las variables por AppDomain y por proceso en código administrado.

- Resuelve los problemas de bloqueo del cargador que se aplican a las DLL mixtas compiladas en Visual Studio 2003 y versiones anteriores.

Además, esta compatibilidad presenta las siguientes limitaciones:

- Solo el modelo del archivo DLL de CRT es compatible para el código compilado con **/CLR**. No hay ninguna bibliotecas CRT estáticas que admiten **/CLR** compilaciones.

## <a name="see-also"></a>Vea también

- [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
