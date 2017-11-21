---
title: "¿Se puede alojar más de un Control en una sola ventana? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fa1a1b914d7d9725e8f2d9858f0481bb7aa24a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>¿Se puede alojar más de un Control en una sola ventana?
No es posible hospedar más de un control en una sola ventana de host ATL. Cada ventana host está diseñada para alojar exactamente un control cada vez (Esto permite que un mecanismo sencillo para administrar las propiedades ambiente de reflexión y por control de mensajes). Sin embargo, si necesita que el usuario vea varios controles en una sola ventana, resulta sencillo crear múltiples ventanas host como elementos secundarios de esa ventana.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

