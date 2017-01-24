---
title: "Running the Program as a Local Server | Microsoft Docs"
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
  - "servicios ATL, running as local servers"
  - "depurar [ATL], running services as local server"
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Running the Program as a Local Server
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si se debe ejecutar el programa como un servicio es complejo, puede cambiar temporalmente el registro para ejecutar el programa como servidor local normal.  Cambie simplemente el valor de `LocalService` bajo el AppID a `_LocalService` y asegúrese de que la clave de `LocalServer32` bajo el CLSID se establece correctamente.  \(Observe que utilice DCOMCNFG especificar que la aplicación se debe ejecutar en un equipo diferente de la clave de `LocalServer32` a `_LocalServer32`.\) Ejecutando el programa como servidor local tarda unos más segundos en inicio porque la llamada a **StartServiceCtrlDispatcher** en `CAtlServiceModuleT::Start` tarda unos segundos antes de que se produzca un error.  
  
## Vea también  
 [Debugging Tips](../atl/debugging-tips.md)