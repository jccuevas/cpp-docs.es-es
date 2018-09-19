---
title: Usar un Control de animación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d6b6b07040fbece5fae24fb2ca6be8985695eb0
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950542"
---
# <a name="using-an-animation-control"></a>Usar un control de animación
Uso típico de un control de animación sigue el modelo siguiente:  
  
-   Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. (Debe tener un [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) miembro en la clase de cuadro de diálogo que se corresponde con el control de animación.) Como alternativa, puede usar el [crear](../mfc/reference/canimatectrl-class.md#create) función de miembro para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Cargue un clip AVI en el control de animación mediante una llamada a la [abiertos](../mfc/reference/canimatectrl-class.md#open) función miembro. Si el control de animación está en un cuadro de diálogo, es un buen lugar para hacer esto en la clase de cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) función.  
  
-   Reproducir el clip mediante una llamada a la [reproducir](../mfc/reference/canimatectrl-class.md#play) función miembro. Si el control de animación está en un cuadro de diálogo, es un buen lugar para hacer esto en la clase de cuadro de diálogo `OnInitDialog` (función). Al llamar a `Play` no es necesario si el control de animación tiene establecido el estilo ACS_AUTOPLAY establecido.  
  
-   Si desea mostrar partes del clip o reproducirlo fotograma a fotograma, utilice la `Seek` función miembro. Para detener un clip que se está reproduciendo, use la `Stop` función miembro.  
  
-   Si no va a destruir el control inmediatamente, quite el clip de la memoria mediante una llamada a la `Close` función miembro.  
  
-   Si el control de animación está en un cuadro de diálogo y el `CAnimateCtrl` automáticamente se destruirá el objeto. Si no es así, debe asegurarse de que tanto el control y la `CAnimateCtrl` objeto se han destruido correctamente. Destruir el control de forma automática, cierra el clip AVI.  
  
## <a name="see-also"></a>Vea también  
 [Usar CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [Controles](../mfc/controls-mfc.md)

