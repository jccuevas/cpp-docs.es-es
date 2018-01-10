---
title: Agregar funcionalidad al Control compuesto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6dcf3ffa0c3168c2f96a3ad9bed13ab1213f63da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-functionality-to-the-composite-control"></a>Agregar funcionalidad al Control compuesto
Una vez que haya insertado todos los controles necesarios en el control compuesto, el siguiente paso implica agregar la nueva funcionalidad. Esta nueva funcionalidad normalmente se divide en dos categorías:  
  
-   Compatibilidad con interfaces adicionales y personalizar el comportamiento de su control compuesto con funciones adicionales y específicas.  
  
-   Control de eventos desde el control ActiveX independiente (o controles).  
  
 Para el propósito y el ámbito de este artículo, el resto de esta sección se centra exclusivamente en el control de eventos de controles ActiveX.  
  
> [!NOTE]
>  Si necesita controlar los mensajes desde los controles de Windows, consulte [implementar una ventana](../atl/implementing-a-window.md) para obtener más información sobre el control de mensajes en ATL.  
  
 Después de insertar un control ActiveX en el recurso de cuadro de diálogo, haga clic en el control y haga clic en **Agregar controlador de eventos**. Seleccione el evento que desee controlar y haga clic en **agregar y editar**. El código del controlador de eventos se agregará al archivo .h del control.  
  
 Puntos de conexión para controles ActiveX en el control compuesto automáticamente están conectados y desconectados mediante llamadas a [CComCompositeControl:: AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de controles compuestos](../atl/atl-composite-control-fundamentals.md)

