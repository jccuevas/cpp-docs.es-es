---
title: ¿Se puede alojar más de un Control en una sola ventana? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ceb9444b6371e261115bbf52ef5a249100772d1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356429"
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>¿Se puede alojar más de un Control en una sola ventana?
No es posible hospedar más de un control en una sola ventana de host ATL. Cada ventana host está diseñada para alojar exactamente un control cada vez (Esto permite que un mecanismo sencillo para administrar las propiedades ambiente de reflexión y por control de mensajes). Sin embargo, si necesita que el usuario vea varios controles en una sola ventana, resulta sencillo crear múltiples ventanas host como elementos secundarios de esa ventana.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

