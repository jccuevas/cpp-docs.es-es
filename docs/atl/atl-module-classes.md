---
title: Clases de módulo de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317370"
---
# <a name="atl-module-classes"></a>Clases de módulo de ATL

En este tema se describen las clases de módulo que eran nuevas en ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Clases de reemplazo de CComModule

Versiones anteriores de `CComModule`ATL utilizadas . En ATL 7.0, `CComModule` la funcionalidad se sustituye por varias clases:

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) Contiene información requerida por la mayoría de las aplicaciones que utilizan ATL. Contiene la HINSTANCE del módulo y la instancia de recurso.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) Contiene información requerida por las clases COM en ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) Contiene información requerida por las clases de ventana en ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) Contiene compatibilidad con la depuración de interfaces.

- [CAtlModule](../atl/reference/catlmodule-class.md) Las `CAtlModule`siguientes clases derivadas se personalizan para contener la información necesaria en un tipo de aplicación determinado. La mayoría de los miembros de estas clases se pueden invalidar:

  - [CAtldllModulet](../atl/reference/catldllmodulet-class.md) Se utiliza en aplicaciones DLL. Proporciona código para las exportaciones estándar.

  - [CAtlexeModuleT](../atl/reference/catlexemodulet-class.md) Se utiliza en aplicaciones EXE. Proporciona el código necesario en un archivo EXE.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Proporciona compatibilidad para crear servicios de Windows NT y Windows 2000.

`CComModule`todavía está disponible para la compatibilidad con versiones anteriores.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Razones para distribuir la funcionalidad de CComModule

La funcionalidad `CComModule` de se distribuyó en varias clases nuevas por las siguientes razones:

- Haga que la `CComModule` funcionalidad sea granular.

   La compatibilidad con las características COM, windowsing, interface debugging y específica de la aplicación (DLL o EXE) ahora está en clases independientes.

- Declare automáticamente la instancia global de cada uno de estos módulos.

   Una instancia global de las clases de módulo necesarias está vinculada al proyecto.

- Elimine la necesidad de llamar a los métodos Init y Term.

   Los métodos Init y Term se han movido a los constructores y destructores de las clases de módulo; ya no es necesario llamar a Init y Term.

## <a name="see-also"></a>Consulte también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[Información general de clases](../atl/atl-class-overview.md)
