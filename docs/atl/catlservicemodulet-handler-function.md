---
title: 'Función CAtlServiceModuleT:: Handler | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
dev_langs:
- C++
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c8dc0b0d41a18c775258e1eacddd8e4dbebdb3d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039223"
---
# <a name="catlservicemodulethandler-function"></a>Función CAtlServiceModuleT:: Handler

`CAtlServiceModuleT::Handler` es la rutina que llama el Administrador de control de servicios (SCM) para recuperar el estado del servicio y darle diversas instrucciones (por ejemplo, detener o pausar). El SCM pasa un código de operación a `Handler` para indicar lo que debe hacer el servicio. Servicio predeterminado generado por ATL sólo controla la instrucción stop. Si el SCM pasa dicha instrucción, el servicio indica el SCM que el programa está a punto de detenerse. El servicio, a continuación, llama a `PostThreadMessage` para publicar un mensaje a sí mismo. Esto finaliza el bucle de mensajes y el servicio se cerrará en última instancia.

Para controlar más instrucciones, deberá cambiar el `m_status` inicializar el miembro de datos en el `CAtlServiceModuleT` constructor. Este miembro de datos indica qué botones se habilita cuando se selecciona el servicio en la aplicación de Panel de Control de servicios de la SCM.

## <a name="see-also"></a>Vea también

[Servicios](../atl/atl-services.md)<br/>
[CAtlServiceModuleT:: Handler](../atl/reference/catlservicemodulet-class.md#handler)

