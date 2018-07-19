---
title: Seleccionar un objeto gráfico en un contexto de dispositivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc605be317d51c985e32fbad038d846b056e5fe6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379689"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Seleccionar un objeto gráfico en un contexto de dispositivo
En este tema se aplica al uso de objetos gráficos en contexto de dispositivo de una ventana. Después de [crear un objeto de dibujo](../mfc/one-stage-and-two-stage-construction-of-objects.md), debe seleccionarlo en el contexto de dispositivo en lugar del objeto predeterminado que se almacenan allí:  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## <a name="lifetime-of-graphic-objects"></a>Duración de objetos gráficos  
 El objeto gráfico devuelto por [SelectObject](../mfc/reference/cdc-class.md#selectobject) es "temporal". Es decir, se eliminará el [OnIdle](../mfc/reference/cwinapp-class.md#onidle) función miembro de clase `CWinApp` hora la próxima vez que el programa obtiene inactivo. Siempre que utilice el objeto devuelto por `SelectObject` en una sola función sin devolver el control al bucle de mensajes principal, no tendrá que no hay ningún problema.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Objetos gráficos](../mfc/graphic-objects.md)  
  
-   [Construcción de una fase y en dos fases de objetos gráficos](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Dibujo en una vista](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>Vea también  
 [Objetos gráficos](../mfc/graphic-objects.md)

