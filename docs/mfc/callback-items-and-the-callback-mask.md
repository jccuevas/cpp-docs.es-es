---
title: Elementos de devolución de llamada y la máscara de devolución de llamada | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95c896308970ffc6a2040657927dc127eee278ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="callback-items-and-the-callback-mask"></a>Elementos de devolución de llamada y máscara de devolución de llamada
Para cada uno de sus elementos, un control de vista de lista suele almacena el texto de etiqueta, el índice de la lista de imágenes de iconos del elemento, y marcas de un conjunto de bits para el estado del elemento. Puede definir elementos individuales como elementos de devolución de llamada, que son útiles si la aplicación ya almacena parte de la información de un elemento.  
  
 Para definir un elemento como un elemento de devolución de llamada, especifique los valores adecuados para el `pszText` y `iImage` los miembros de la **LV_ITEM** estructura (vea [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)). Si la aplicación mantiene el texto del elemento o del subelemento, especifique el **LPSTR_TEXTCALLBACK** valor para el `pszText` miembro. Si la aplicación realiza un seguimiento del icono para el elemento, especifique el **I_IMAGECALLBACK** valor para el `iImage` miembro.  
  
 Además de definir elementos de devolución de llamada, también puede modificar la máscara de devolución de llamada del control. Esta máscara es un conjunto de marcadores de bits que especifica los Estados de elemento para el que la aplicación, en lugar de control, almacena los datos actuales. La máscara de devolución de llamada se aplica a todos los elementos del control, a diferencia de la designación de elemento de devolución de llamada, que se aplica a un elemento específico. La máscara de devolución de llamada es cero de forma predeterminada, lo que significa que el control realiza un seguimiento de todos los Estados del elemento. Para cambiar este comportamiento predeterminado, inicialice la máscara para cualquier combinación de los siguientes valores:  
  
-   `LVIS_CUT` El elemento se marca para una operación de cortar y pegar.  
  
-   `LVIS_DROPHILITED` Se resalta el elemento como un destino de arrastrar y colocar.  
  
-   `LVIS_FOCUSED` El elemento tiene el foco.  
  
-   `LVIS_SELECTED` El elemento está seleccionado.  
  
-   **LVIS_OVERLAYMASK** la aplicación almacena el índice de la imagen de superposición actual para cada elemento de lista de imágenes.  
  
-   **LVIS_OVERLAYMASK** la aplicación almacena el índice de la imagen del estado actual para cada elemento de lista de imágenes.  
  
 Para obtener más información sobre la recuperación y configuración de esta máscara, consulte [CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) y [CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

