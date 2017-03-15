---
title: "CAtlServiceModuleT::ServiceMain Function | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceMain"
  - "CServiceModule::ServiceMain"
  - "CServiceModule.ServiceMain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ServiceMain method"
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CAtlServiceModuleT::ServiceMain Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El administrador \(SCM\) de control de servicios llama `ServiceMain` cuando se abra la aplicación del Panel de control de Servicios, seleccione el servicio, haga clic en **Iniciar**.  
  
 Después de que SCM llame a `ServiceMain`, un servicio debe otorgarle SCM una función controladora.  Esta función permite SCM obtener el estado del servicio y pasar instrucciones concretas \(como pausar o detener\).  SCM obtiene esta función cuando el servicio pasa **\_Handler** a la función de la API Win32, [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054).  \(**\_Handler** es una función miembro estática que llama a la función instancias [controlador](../atl/catlservicemodulet-handler-function.md)miembro.\)  
  
 En el inicio, un servicio también debe informar a SCM su estado actual.  Haga esto pasando **SERVICE\_START\_PENDING** a la función de la API Win32, [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain` llama `CAtlExeModuleT::InitializeCom`, que llama a la función [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)de la API Win32.  de forma predeterminada, `InitializeCom` pasa el indicador de **COINIT\_MULTITHREADED** a la función.  Este mensaje indica que el programa se servidor de subprocesamiento libre.  
  
 Ahora, `CAtlServiceModuleT::Run` se llama para realizar el trabajo principal del servicio.  **Ejecutar** continúa ejecutándose hasta que se detenga el servicio.  
  
## Vea también  
 [Servicios](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../Topic/CAtlServiceModuleT::ServiceMain.md)