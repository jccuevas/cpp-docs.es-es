---
title: Servicios ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule
dev_langs:
- C++
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4875c4844b97e3715c3804f83f4fa3e863eb53bc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761035"
---
# <a name="atl-services"></a>Servicios ATL

Para crear un objeto ATL COM para que se ejecute en un servicio, simplemente seleccione servicio (EXE) en la lista de opciones de servidor en el Asistente para proyectos ATL. El asistente, a continuación, creará una clase derivada de `CAtlServiceModuleT` para implementar el servicio.

Cuando el objeto COM de ATL se compila como un servicio, solo se registrará como un servidor local y no aparecerán en la lista de servicios en el Panel de Control. Esto es porque es más fácil de depurar el servicio como un servidor local que como un servicio. Para instalarlo como un servicio, ejecute lo siguiente en el símbolo del sistema:

`YourEXE` `.exe /Service`

Para desinstalarla, ejecute lo siguiente:

`YourEXE` `.exe /UnregServer`

Los primeros cuatro temas en esta sección tratan las acciones que se producen durante la ejecución de `CAtlServiceModuleT` funciones miembro. Estos temas aparecen en la misma secuencia, como las funciones se suelen denominar simplemente. Para mejorar la comprensión de estos temas, es una buena idea usar el código fuente generado por el Asistente para proyectos de ATL como referencia. Los cuatro primeros temas son:

- [La función CAtlServiceModuleT:: Start](../atl/reference/catlservicemodulet-class.md#start)

- [La función CAtlServiceModuleT:: ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

- [La función CAtlServiceModuleT:: Run](../atl/reference/catlservicemodulet-class.md#run)

- [La función CAtlServiceModuleT:: Handler](../atl/reference/catlservicemodulet-class.md#handler)

Los tres últimos temas explican conceptos relacionados con el desarrollo de un servicio:

- [Las entradas del registro](../atl/registry-entries.md) para servicios ATL

- [DCOMCNFG](../atl/dcomcnfg.md)

- [Sugerencias de depuración](../atl/debugging-tips.md) para servicios ATL

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)

