---
title: Agregar funcionalidad al Control compuesto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67602e16fc5a30c82e82772b6b9f6c553ba79d9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

