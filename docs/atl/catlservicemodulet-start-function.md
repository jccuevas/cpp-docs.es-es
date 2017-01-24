---
title: "CAtlServiceModuleT::Start Function | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CServiceModule.Start"
  - "CServiceModule::Start"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Start (método)"
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlServiceModuleT::Start Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se ejecuta el servicio, **\_tWinMain** llama **CAtlServiceModuleT:: WinMain**, que a su vez llama a `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start` coloca una matriz de estructuras de **SERVICE\_TABLE\_ENTRY** que asignan cada servicio a la función de inicio.  Esta matriz se pasa a la función de la API Win32, [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324).  En teoría, un EXE podría controlar de varios servicios y la matriz podría tener varias estructuras de **SERVICE\_TABLE\_ENTRY** .  Actualmente, sin embargo, un servicio ATL\-generado sólo admite un servicio mediante un archivo EXE.  Por consiguiente, la matriz tiene una entrada única que contiene el nombre y **\_ServiceMain** de servicio como función de inicio.  **\_ServiceMain** es una función miembro estática de `CAtlServiceModuleT` que llama a la función miembro no estática, `ServiceMain`.  
  
> [!NOTE]
>  El error de **StartServiceCtrlDispatcher** conectarse al administrador de control \(SCM\) de servicios significa probable que el programa no se ejecuta como servicio.  En este caso, el programa llama a `CAtlServiceModuleT::Run` directamente de modo que el programa pueda ejecutarse como un servidor local.  Para obtener más información sobre cómo ejecutar el programa como servidor local, vea [Sugerencias de depuración](../atl/debugging-tips.md).  
  
## Vea también  
 [Servicios](../atl/atl-services.md)   
 [CAtlServiceModuleT::Start](../Topic/CAtlServiceModuleT::Start.md)