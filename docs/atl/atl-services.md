---
title: Servicios ATL
ms.date: 11/04/2016
f1_keywords:
- CServiceModule
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 3308e7fb38dfaab13c2570f216772e2af459a7f2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273665"
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
