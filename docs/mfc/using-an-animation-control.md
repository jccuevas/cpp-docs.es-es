---
title: "Usar un Control de animación | Documentos de Microsoft"
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
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38523c832f4a30f247bd3e1d0b8318f44f5c47b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-animation-control"></a>Usar un control de animación
Uso típico de un control de animación sigue el modelo siguiente:  
  
-   Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. (Debe tener un [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) miembro en la clase de cuadro de diálogo que se corresponde con el control de animación.) Como alternativa, puede usar el [crear](../mfc/reference/canimatectrl-class.md#create) función de miembro para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Cargue un clip AVI en el control de animación mediante una llamada a la [abiertos](../mfc/reference/canimatectrl-class.md#open) función miembro. Si el control de animación está en un cuadro de diálogo, es un buen lugar para hacer esto en la clase de cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) función.  
  
-   Reproducir el clip mediante una llamada a la [reproducir](../mfc/reference/canimatectrl-class.md#play) función miembro. Si el control de animación está en un cuadro de diálogo, es un buen lugar para hacer esto en la clase de cuadro de diálogo **OnInitDialog** función. Al llamar a **reproducir** no es necesario si el control de animación tiene la `ACS_AUTOPLAY` conjunto de estilo.  
  
-   Si desea mostrar partes del clip o reproducirlo fotograma a fotograma, utilice la `Seek` función miembro. Para detener un clip que se está reproduciendo, use la `Stop` función miembro.  
  
-   Si no va a destruir el control inmediatamente, quite el clip de la memoria mediante una llamada a la **cerrar** función miembro.  
  
-   Si el control de animación está en un cuadro de diálogo y el `CAnimateCtrl` automáticamente se destruirá el objeto. Si no es así, debe asegurarse de que tanto el control y la `CAnimateCtrl` objeto se han destruido correctamente. Destruir el control de forma automática, cierra el clip AVI.  
  
## <a name="see-also"></a>Vea también  
 [Usar CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Controles](../mfc/controls-mfc.md)

