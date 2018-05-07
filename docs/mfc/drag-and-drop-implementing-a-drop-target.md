---
title: 'Arrastrar y colocar: implementar un destino de colocación | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 414437f044869fef7ae48883a88688ad50c9ac5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Arrastrar y colocar: Implementar un destino de colocación
En este artículo se describe cómo hacer que su aplicación un destino de colocación. Implementar un destino de colocación tarda un poco más compleja que la implementación de un origen de colocación, pero sigue siendo relativamente sencilla. Estas técnicas también se aplican a aplicaciones no compatibles con OLE.  
  
#### <a name="to-implement-a-drop-target"></a>Para implementar un destino de colocación  
  
1.  Agregue una variable miembro a cada vista en la aplicación que se va a ser un destino de colocación. Esta variable miembro debe ser de tipo `COleDropTarget` o una clase derivada de ella.  
  
2.  En función de la clase de vista que controla el `WM_CREATE` mensaje (normalmente `OnCreate`), llame a la nueva variable miembro `Register` función miembro. `Revoke` se llamará automáticamente para usted cuando se destruye la vista.  
  
3.  Invalidar las siguientes funciones. Si desea que el mismo comportamiento en toda la aplicación, reemplace estas funciones en la clase de vista. Si desea modificar el comportamiento en casos aislados o desea habilitar la eliminación en no es`CView` windows, reemplace estas funciones en su `COleDropTarget`-clase derivada.  
  
    |invalidación|Para permitir|  
    |--------------|--------------|  
    |`OnDragEnter`|Quitar las operaciones que se produzca en la ventana. Se llama cuando el cursor entra por primera vez la ventana.|  
    |`OnDragLeave`|Comportamiento especial cuando la operación de arrastre sale de la ventana especificada.|  
    |`OnDragOver`|Quitar las operaciones que se produzca en la ventana. Se llama cuando se arrastra el cursor en la ventana.|  
    |`OnDrop`|Tratamiento de los datos que se va a colocar en la ventana especificada.|  
    |`OnScrollBy`|Comportamiento especial cuando desplazamiento es necesario en la ventana de destino.|  
  
 Consulte la MAINVIEW. CPP archivo que forma parte de la muestra de OLE de MFC [OCLIENT](../visual-cpp-samples.md) para obtener un ejemplo de cómo funcionan estas características conjuntamente.  
  
 Para obtener más información, consulte:  
  
-   [Implementar un origen de colocación](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Crear y destruir objetos de datos OLE y orígenes de datos](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Manipular objetos de datos OLE y orígenes de datos](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>Vea también  
 [Arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget (clase)](../mfc/reference/coledroptarget-class.md)
