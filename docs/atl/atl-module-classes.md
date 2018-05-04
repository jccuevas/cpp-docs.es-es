---
title: Clases de módulo ATL | Documentos de Microsoft
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
ms.openlocfilehash: 777d81fbe1de48289863fda00591a5328b40cf4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="atl-module-classes"></a>Clases de módulo de ATL
Este tema describen las clases de módulo que se introdujeron en ATL 7.0.  
  
## <a name="ccommodule-replacement-classes"></a>Clases de reemplazo de CComModule  
 Las versiones anteriores de ATL usa `CComModule`. En ATL 7.0, `CComModule` funcionalidad se ha reemplazado por varias clases:  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) contiene información requerida por la mayoría de las aplicaciones que utilizan ATL. Contiene la HINSTANCE del módulo y la instancia del recurso.  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md) contiene información requerida por las clases COM de ATL.  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md) contiene información requerida por las clases de ventana de ATL.  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) contiene compatibilidad para la depuración de interfaz.  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md) siguiente `CAtlModule`-clases derivadas están personalizadas para que contenga la información necesaria en un tipo de aplicación en particular. Se puede invalidar la mayoría de los miembros de estas clases:  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) usar en aplicaciones de DLL. Proporciona código para las exportaciones estándares.  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) utilizado en las aplicaciones EXE. Proporciona el código requerido en un archivo EXE.  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) proporciona compatibilidad para crear servicios Windows NT y Windows 2000.  
  
 `CComModule` sigue estando disponible para compatibilidad con versiones anteriores.  
  
## <a name="reasons-for-distributing-ccommodule-functionality"></a>Motivos para la distribución de la funcionalidad de CComModule  
 La funcionalidad de `CComModule` se ha distribuido en varias clases nuevas para los siguientes motivos:  
  
-   Realizar la funcionalidad de `CComModule` granular.  
  
     Compatibilidad con COM, basado en ventanas, depuración de interfaces y características de específicos de la aplicación (DLL o EXE) se encuentra ahora en clases independientes.  
  
-   Declarar automáticamente la instancia global de cada uno de estos módulos.  
  
     Una instancia global de las clases de módulo requeridas está vinculada en el proyecto.  
  
-   Eliminar la necesidad de llamar a los métodos Init y Term.  
  
     Los métodos Init y Term han movido a los constructores y destructores para las clases de módulo; ya no es necesario llamar a Init y Term.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Información general de clases](../atl/atl-class-overview.md)

