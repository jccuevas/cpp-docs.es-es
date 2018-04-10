---
title: Evitar las excepciones producidas por objetos COM compilados con clr-| Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 287c9831f8c604272b37ac85528d66fe640de557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Evitar excepciones al apagar CLR cuando se utilizan objetos COM compilados con /clr
Una vez que common language runtime (CLR) pasa al modo de apagado, las funciones nativas tienen acceso limitado a los servicios de CLR. Al intentar llamar a Release en un objeto COM compilado con **/CLR**, el CLR realiza la transición a código nativo y, a continuación, vuelve al código administrado para atender la llamada IUnknown:: Release (que se define en código administrado). CLR evita la devolución de llamada a código administrado porque está en modo de apagado.  
  
 Para resolver este problema, asegúrese de que los destructores llamados desde los métodos Release solo contienen código nativo.  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)