---
title: 'Función CAtlServiceModuleT:: Handler'
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: e344fd36ad6c70a80486eef6a10eacd8a88a2baf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273379"
---
# <a name="catlservicemodulethandler-function"></a>Función CAtlServiceModuleT:: Handler

`CAtlServiceModuleT::Handler` es la rutina que llama el Administrador de control de servicios (SCM) para recuperar el estado del servicio y darle diversas instrucciones (por ejemplo, detener o pausar). El SCM pasa un código de operación a `Handler` para indicar lo que debe hacer el servicio. Servicio predeterminado generado por ATL sólo controla la instrucción stop. Si el SCM pasa dicha instrucción, el servicio indica el SCM que el programa está a punto de detenerse. El servicio, a continuación, llama a `PostThreadMessage` para publicar un mensaje a sí mismo. Esto finaliza el bucle de mensajes y el servicio se cerrará en última instancia.

Para controlar más instrucciones, deberá cambiar el `m_status` inicializar el miembro de datos en el `CAtlServiceModuleT` constructor. Este miembro de datos indica qué botones se habilita cuando se selecciona el servicio en la aplicación de Panel de Control de servicios de la SCM.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)
