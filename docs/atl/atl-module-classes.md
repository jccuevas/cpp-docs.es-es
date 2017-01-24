---
title: "Clases de m&#243;dulo de ATL | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, clases module"
  - "CComModule (clase), cambios"
  - "clases module"
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de m&#243;dulo de ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema describe las clases del módulo que eran nuevas en ATL 7,0.  
  
## Clases de reemplazo de CComModule  
 versiones anteriores de `CComModule`utilizado ATL.  En ATL 7,0, la funcionalidad de `CComModule` se reemplaza por varias clases:  
  
-   Información de[CAtlBaseModule](../atl/reference/catlbasemodule-class.md) Contains requerida por la mayoría de las aplicaciones que utilizan ATL.  Contiene el HINSTANCE del módulo y de la instancia de recursos.  
  
-   Información de[CAtlComModule](../atl/reference/catlcommodule-class.md) Contains requerida por las clases COM de ATL.  
  
-   La información de[CAtlWinModule](../atl/reference/catlwinmodule-class.md) Contains requerida por la visualización en una ventana ordena en ATL.  
  
-   Compatibilidad de[CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) Contains para la depuración de la interfaz.  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md) The que sigue `CAtlModule`\- clases derivadas están personalizados para contener la información necesaria en un tipo de aplicación determinado.  La mayoría de los miembros de estas clases se pueden reemplazar:  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) utilizado en aplicaciones de DLL.  Proporciona código para exportaciones estándar.  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) utilizado en aplicaciones EXE.  Proporciona el código necesario en EXE.  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) permite crear Windows NT y Windows 2000 Services.  
  
 `CComModule` aún está disponible para la compatibilidad con versiones anteriores.  
  
## Razones para distribuir la funcionalidad de CComModule  
 La funcionalidad de `CComModule` se distribuida en varias clases nuevas por las razones siguientes:  
  
-   Cree la funcionalidad en `CComModule` concreta.  
  
     Compatibilidad con COM, las operaciones de ventanas, la depuración de interfaz, y \(DLL o EXE\) características específicas de la aplicación es ahora en clases independientes.  
  
-   automáticamente declare la instancia global de cada uno de estos módulos.  
  
     Una instancia global de las clases necesarias de módulo se vincula en el proyecto.  
  
-   Quite la necesidad de llamar a los métodos de Init y el término.  
  
     Los métodos de Init y el término se han movido a los constructores y destructores para las clases del módulo; ya no existe una necesidad de llamar a Init y término.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [Class Overview](../atl/atl-class-overview.md)