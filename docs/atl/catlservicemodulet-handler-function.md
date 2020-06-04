---
title: 'Función CAtlServiceModuleT:: Handler'
ms.date: 11/04/2016
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: fffdeddce7f3fa27d798ea7abafe85c9a13d9d97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223190"
---
# <a name="catlservicemodulethandler-function"></a>Función CAtlServiceModuleT:: Handler

`CAtlServiceModuleT::Handler` es la rutina que llama el Administrador de control de servicios (SCM) para recuperar el estado del servicio y darle diversas instrucciones (por ejemplo, detener o pausar). El SCM pasa un código de operación a `Handler` para indicar lo que debe hacer el servicio. Servicio predeterminado generado por ATL sólo controla la instrucción stop. Si el SCM pasa dicha instrucción, el servicio indica el SCM que el programa está a punto de detenerse. El servicio, a continuación, llama a `PostThreadMessage` para publicar un mensaje a sí mismo. Esto finaliza el bucle de mensajes y el servicio se cerrará en última instancia.

Para controlar más instrucciones, deberá cambiar el `m_status` inicializar el miembro de datos en el `CAtlServiceModuleT` constructor. Este miembro de datos indica qué botones se habilita cuando se selecciona el servicio en la aplicación de Panel de Control de servicios de la SCM.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)
