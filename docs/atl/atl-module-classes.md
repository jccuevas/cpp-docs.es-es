---
title: Clases de módulo de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2fe659b47893f821aab4cda31ab1a4e9a6788ec6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252075"
---
# <a name="atl-module-classes"></a>Clases de módulo de ATL

En este tema se describe las clases de módulo que se introdujeron en ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Clases de reemplazo de CComModule

Las versiones anteriores de ATL utiliza `CComModule`. En ATL 7.0, `CComModule` funcionalidad se ha reemplazado por varias clases:

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) contiene información requerida por la mayoría de las aplicaciones que utilizan ATL. Contiene la HINSTANCE del módulo y la instancia del recurso.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) contiene información requerida por las clases COM de ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) contiene información requerida por las clases de ventanas en ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) contiene compatibilidad para la depuración de interfaz.

- [CAtlModule](../atl/reference/catlmodule-class.md) siguiente `CAtlModule`-las clases derivadas se personalizan para que contenga la información necesaria en un tipo de aplicación concreto. Se pueden invalidar los miembros de la mayoría de estas clases:

   - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) utilizados en las aplicaciones DLL. Proporciona código para las exportaciones estándares.

   - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) utilizado en las aplicaciones EXE. Proporciona el código necesario en un archivo EXE.

   - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) proporciona compatibilidad para crear servicios de Windows 2000 y de Windows NT.

`CComModule` sigue estando disponible para compatibilidad con versiones anteriores.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Motivos para la distribución de la funcionalidad de CComModule

La funcionalidad de `CComModule` se ha distribuido en varias clases nuevas para los siguientes motivos:

- Realizar la funcionalidad en `CComModule` granular.

   Compatibilidad con COM, ventanas, depuración de la interfaz y las características específicas de la aplicación de (DLL o EXE) está ahora en clases independientes.

- Automáticamente, declare una instancia global de cada uno de estos módulos.

   Una instancia global de las clases de módulo necesario está vinculada al proyecto.

- Eliminan la necesidad de llamar a métodos Init y término.

   Los métodos Init y término se han movido a los constructores y destructores para las clases de módulo; ya no hay necesidad de llamar a Init y término.

## <a name="see-also"></a>Vea también

[Conceptos](../atl/active-template-library-atl-concepts.md)<br/>
[Información general de clases](../atl/atl-class-overview.md)
