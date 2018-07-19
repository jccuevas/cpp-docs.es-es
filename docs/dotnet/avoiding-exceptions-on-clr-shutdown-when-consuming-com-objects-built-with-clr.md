---
title: Evitar las excepciones producidas por objetos COM compilados con clr-| Documentos de Microsoft
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
ms.openlocfilehash: 0efd2af7eb4bf8a70bff983d627f802f1976c6ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103517"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con /clr
Una vez que common language runtime (CLR) pasa al modo de apagado, las funciones nativas tienen acceso limitado a los servicios de CLR. Al intentar llamar a Release en un objeto COM compilado con **/CLR**, el CLR realiza la transición a código nativo y, a continuación, vuelve al código administrado para atender la llamada IUnknown:: Release (que se define en código administrado). CLR evita la devolución de llamada a código administrado porque está en modo de apagado.  
  
 Para resolver este problema, asegúrese de que los destructores llamados desde los métodos Release solo contienen código nativo.  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)