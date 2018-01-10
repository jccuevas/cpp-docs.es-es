---
title: "Función CAtlServiceModuleT | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs: C++
helpviewer_keywords: ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 633e9bc4689ced93e1c22151b32654f7ae9d7ece
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemoduletservicemain-function"></a>Función CAtlServiceModuleT
El Administrador de control de servicios (SCM) llama `ServiceMain` cuando se abre la aplicación de Panel de Control de servicios, seleccione el servicio y haga clic en **iniciar**.  
  
 Después el SCM llama `ServiceMain`, un servicio debe darle al SCM una función de controlador. Esta función permite al SCM obtener el estado del servicio y pasar instrucciones específicas (por ejemplo, pausar o detener). El SCM obtiene esta función cuando el servicio pasa **_Handler** a la función API de Win32, [RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054). (**_Handler** es una función miembro estática que llama a la función miembro no estática [controlador](../atl/reference/catlservicemodulet-class.md#handler).)  
  
 Al iniciarse, un servicio también debe informar al SCM de su estado actual. Para ello, pase **SERVICE_START_PENDING** a la función API de Win32, [SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241).  
  
 `ServiceMain`a continuación, llama `CAtlExeModuleT::InitializeCom`, que llama a la función API de Win32 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279). De forma predeterminada, `InitializeCom` pasa el **COINIT_MULTITHREADED** marca a la función. Esta marca indica que el programa para que sea un servidor de subprocesamiento libre.  
  
 Ahora, `CAtlServiceModuleT::Run` se llama para realizar el trabajo principal del servicio. **Ejecutar** continúa ejecutándose hasta que el servicio está detenido.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de](../atl/atl-services.md)   
 [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md#servicemain)

