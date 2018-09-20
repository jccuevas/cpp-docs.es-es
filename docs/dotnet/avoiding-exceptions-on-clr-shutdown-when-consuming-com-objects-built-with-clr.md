---
title: Evitar las excepciones producidas por objetos COM compilados con - clr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 687585d0b25c64f5575646de3cd4823e0a89988e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408991"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con /clr

Una vez que common language runtime (CLR) entra en modo de apagado, las funciones nativas tienen acceso limitado a los servicios de CLR. Cuando se intenta llamar a Release en un objeto COM compilado con **/CLR**, el CLR realiza la transición a código nativo y, a continuación, vuelve al código administrado para atender la llamada de IUnknown:: Release (que se define en código administrado). El CLR impide que la devolución de llamada a código administrado, ya que resulta en modo de apagado.

Para resolver este problema, asegúrese de que los destructores se llama desde métodos versión sólo contienen código nativo.

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)