---
title: "Función CAtlServiceModuleT:: Handler | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs: C++
helpviewer_keywords: Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 00158bbed5318d919c284b91cd651141a35bd441
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlservicemodulethandler-function"></a>Función CAtlServiceModuleT:: Handler
`CAtlServiceModuleT::Handler`es la rutina que el Administrador de control de servicios (SCM) llama para recuperar el estado del servicio y darle diversas instrucciones (por ejemplo, detener o pausar). El SCM pasa un código de operación a `Handler` para indicar lo que debe hacer el servicio. Servicio generado con ATL predeterminado sólo controla la instrucción stop. Si el SCM pasa la instrucción stop, el servicio indica al SCM que el programa está a punto de detenerse. El servicio, a continuación, llama a `PostThreadMessage` para enviar un mensaje de finalización a sí mismo. Esto finaliza el bucle de mensajes y el servicio se cerrará en última instancia.  
  
 Para controlar más instrucciones, debe cambiar la `m_status` inicializar el miembro de datos en el `CAtlServiceModuleT` constructor. Este miembro de datos indica al SCM los botones que deben habilitar cuando se selecciona el servicio en la aplicación del Panel de Control de servicios.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de](../atl/atl-services.md)   
 [CAtlServiceModuleT:: Handler](../atl/reference/catlservicemodulet-class.md#handler)

