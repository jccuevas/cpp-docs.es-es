---
title: "Función CAtlServiceModuleT:: Start | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
dev_langs: C++
helpviewer_keywords: Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d4ee7899cda213bf8d8cfd529fd7609976e20d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemoduletstart-function"></a>Función CAtlServiceModuleT:: Start
Cuando se ejecuta el servicio, **_tWinMain** llamadas **a CAtlServiceModuleT:: WinMain**, que a su vez, llama `CAtlServiceModuleT::Start`.  
  
 `CAtlServiceModuleT::Start`establece la matriz de **SERVICE_TABLE_ENTRY** estructuras que se asignan cada servicio a su función de inicio. Esta matriz, a continuación, se pasa a la función API de Win32, [StartServiceCtrlDispatcher](http://msdn.microsoft.com/library/windows/desktop/ms686324). En teoría, un archivo EXE puede controlar varios servicios y la matriz puede tener varias **SERVICE_TABLE_ENTRY** estructuras. En la actualidad, sin embargo, un servicio generado con ATL sólo admite un servicio por archivo EXE. Por lo tanto, la matriz tiene una única entrada que contiene el nombre del servicio y **_ServiceMain** como la función de inicio. **_ServiceMain** es una función miembro estática de `CAtlServiceModuleT` que llama a la función miembro no estática, `ServiceMain`.  
  
> [!NOTE]
>  Error de **StartServiceCtrlDispatcher** para conectar con el control de service manager (SCM) probablemente indica que el programa no se ejecuta como un servicio. En este caso, el programa llama `CAtlServiceModuleT::Run` directamente para que el programa puede ejecutarse como un servidor local. Para obtener más información acerca de cómo ejecutar el programa como un servidor local, vea [sugerencias de depuración](../atl/debugging-tips.md).  
  
## <a name="see-also"></a>Vea también  
 [Servicios de](../atl/atl-services.md)   
 [CAtlServiceModuleT:: Start](../atl/reference/catlservicemodulet-class.md#start)

