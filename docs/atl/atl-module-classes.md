---
title: "Clases de módulo ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b254edfe75cfcdaee7ab15351f7c05c3d163e301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 `CComModule`sigue estando disponible para compatibilidad con versiones anteriores.  
  
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

