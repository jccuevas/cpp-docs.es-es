---
title: Clases de módulo ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e885ef1db8f282bbdca2e8c39c3d1221d791d1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067641"
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

