---
title: "¿Qué es un objeto de Host? (ATL) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- host objects
ms.assetid: 4f8da992-b27e-45e8-b5e0-c8b1dcae4fac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da735caa84c133b9cdf63fae5df8bdd3d5f774b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-host-object"></a>¿Qué es un objeto de Host?
Un objeto de host es un objeto COM que representa el contenedor de controles ActiveX suministrado por ATL para una ventana concreta. El objeto host subclases de la ventana del contenedor para que pueda reflejar mensajes al control, proporciona las interfaces contenedoras necesarias para ser utilizados por el control y expone el [interfaces IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) y [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfaces para permitirle configurar el entorno del control.  
  
 Puede usar el objeto host para establecer las propiedades de ambiente del contenedor.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)

