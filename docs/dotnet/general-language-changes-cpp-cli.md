---
title: Cambios generales en el lenguaje (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b48ebdf0bf25399b08f8a1cb1240a857cfad352
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418468"
---
# <a name="general-language-changes-ccli"></a>Cambios generales en el lenguaje (C++/CLI)

Un número de características del lenguaje CLR cambiado de extensiones administradas para C++ a Visual C++.

Los cambios descritos en esta sección son una especie de Miscelánea del lenguaje. Incluye un cambio en el control de los literales de cadena, un cambio en la resolución de sobrecarga entre los puntos suspensivos y la `Param` atributo, el cambio de `typeof` a `typeid`, un cambio en la llamada de las listas de inicializadores de constructor y el Introducción de una nueva notación de conversión de `safe_cast`.

[Literal de cadena](../dotnet/string-literal.md)<br/>
Describe cómo ha cambiado el control de literales de cadena.

[Matriz de parámetros y puntos suspensivos](../dotnet/param-array-and-ellipsis.md)<br/>
Describe cómo `ParamArray` ahora tiene prioridad sobre los puntos suspensivos (`...`) para resolver las llamadas de función con un número variable de argumentos.

[T::typeid reemplaza a typeof](../dotnet/typeof-goes-to-t-typeid.md)<br/>
Describe cómo el `typeof` ha suplantado al operador `typeid`.

[Listas de inicializadores](../dotnet/initializer-lists.md)<br/>
Describe los cambios en el orden de las listas de inicializadores que realiza la llamada.

[Notación de conversión e introducción de safe_cast<>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<br/>
Se describen los cambios en la notación de conversión y, en particular la introducción de `safe_cast`.

## <a name="see-also"></a>Vea también

[Manual de migraciones C++/CLI](../dotnet/cpp-cli-migration-primer.md)