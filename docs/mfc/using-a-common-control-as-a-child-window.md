---
title: Usar un Control común como ventana secundaria | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50d21675d913211026a2077a0830b7d8ed1225c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-common-control-as-a-child-window"></a>Usar un control común como ventana secundaria
Cualquiera de los controles comunes de Windows se puede usar como una ventana secundaria de cualquier otra ventana. El siguiente procedimiento describe cómo crear un control común de forma dinámica y, a continuación, trabajar con ella.  
  
### <a name="to-use-a-common-control-as-a-child-window"></a>Para utilizar un control común como ventana secundaria  
  
1.  Defina el control de la clase relacionada o el controlador.  
  
2.  Use la invalidación del control de la [CWnd:: Create](../mfc/reference/cwnd-class.md#create) método para crear el control de Windows.  
  
3.  Una vez creado el control (tan pronto como el `OnCreate` controlador si subclase del control), puede manipular el control mediante sus funciones miembro. Vea las descripciones de los controles individuales en [controles](../mfc/controls-mfc.md) para obtener más información sobre los métodos.  
  
4.  Cuando haya terminado con el control, use [CWnd:: DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) para destruir el control.  
  
## <a name="see-also"></a>Vea también  
 [Crear y utilizar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)

