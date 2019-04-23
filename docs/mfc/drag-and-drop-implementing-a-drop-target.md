---
title: 'Arrastrar y colocar: Implementar un destino de colocación'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
ms.openlocfilehash: 46501193569d7f3098e23c67c68c76ce20a82ea3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58766682"
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Arrastrar y colocar: Implementar un destino de colocación

En este artículo se describe cómo hacer que la aplicación en un destino de colocación. Implementar un destino de colocación tarda un poco más compleja que la implementación de un origen de colocación, pero es relativamente sencillo. Estas técnicas también se aplican a las aplicaciones que no son compatibles con OLE.

#### <a name="to-implement-a-drop-target"></a>Para implementar un destino de colocación

1. Agregue una variable miembro a cada vista en la aplicación que desea que sea un destino de colocación. Esta variable miembro debe ser de tipo `COleDropTarget` o una clase derivada de él.

1. En función de la clase de vista que controla la **WM_CREATE** mensaje (normalmente `OnCreate`), llame a la nueva variable miembro `Register` función miembro. `Revoke` se llamará automáticamente para usted cuando se destruye la vista.

1. Invalidar las funciones siguientes. Si desea que el mismo comportamiento en toda la aplicación, reemplace estas funciones en la clase de vista. Si desea modificar el comportamiento en casos aislados, o desea habilitar la eliminación en que no sean de`CView` windows, reemplace estas funciones en su `COleDropTarget`-clase derivada.

    |invalidar|Para permitir|
    |--------------|--------------|
    |`OnDragEnter`|Quitar las operaciones que se produzca en la ventana. Se llama cuando el cursor entra por primera vez la ventana.|
    |`OnDragLeave`|Comportamiento especial cuando sale de la operación de arrastrar la ventana especificada.|
    |`OnDragOver`|Quitar las operaciones que se produzca en la ventana. Se llama cuando se arrastra el cursor en la ventana.|
    |`OnDrop`|Control de datos que se va a colocar en la ventana especificada.|
    |`OnScrollBy`|Comportamiento especial cuando el desplazamiento es necesario en la ventana de destino.|

Consulte MAINVIEW. Archivo de CPP que forma parte de la muestra de OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) para obtener un ejemplo de cómo funcionan conjuntamente estas funciones.

Para obtener más información, consulte:

- [Implementación de un origen de colocación](../mfc/drag-and-drop-implementing-a-drop-source.md)

- [Crear y destruir objetos de datos OLE y orígenes de datos](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipular objetos de datos OLE y orígenes de datos](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Vea también

[Arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropTarget (clase)](../mfc/reference/coledroptarget-class.md)
