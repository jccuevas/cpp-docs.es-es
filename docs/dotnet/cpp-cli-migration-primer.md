---
title: C++ / c++ / CLI Migration Primer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88b32ea226971c0fa5b6d269a8992629c3c4de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385436"
---
# <a name="ccli-migration-primer"></a>Manual de migraciones C++/CLI

Esta es una guía para mover sus programas de Visual C++ de extensiones administradas para C++ a Visual C++.

C++ / c++ / CLI amplía un paradigma de programación de componente dinámico al lenguaje estándar ISO C++. El nuevo lenguaje ofrece varias mejoras significativas en las extensiones administradas. Esta sección proporciona una lista de las extensiones administradas para características del lenguaje C++ y su asignación a Visual C++, donde existe este tipo de asignación y destaca las construcciones que no existe ninguna asignación.

## <a name="in-this-section"></a>En esta sección

[Esquema de cambios (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)<br/>
Un esquema general de referencia rápida, que proporciona una lista de los cambios bajo cinco categorías generales.

[Palabras clave del lenguaje (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)<br/>
Describe los cambios de palabras clave del lenguaje, incluida la eliminación del subrayado doble y la introducción de las palabras clave contextuales y espaciadas.

[Tipos administrados (C++ / c++ / CL)](../dotnet/managed-types-cpp-cl.md)<br/>
Explica los cambios sintácticos en la declaración de la Common Type System (CTS): Esto incluye los cambios en la declaración de clases, matrices (incluida la matriz de parámetros), enumeraciones y así sucesivamente.

[Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
Presenta los cambios que afectan a los miembros de clase, como propiedades escalares, propiedades del índice, operadores, delegados y eventos.

[Tipos de valor y su comportamiento (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Se centra en los tipos de valor y la nueva familia de punteros interiores y anclados. También describe una serie de cambios semánticos importantes como la introducción de la conversión boxing implícita, la inmutabilidad de tipos de valor con conversión boxing y la eliminación de la compatibilidad con constructores predeterminados dentro de las clases de valor.

[Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
Detalla cambios semánticos como la compatibilidad con la notación de conversión de cadena literal comportamiento y cambios semánticos entre ISO-C++ y C++ / c++ / CLI.

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)