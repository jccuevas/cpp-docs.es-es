---
title: 'Arrastrar y colocar: Implementación de un origen de colocación'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE drag and drop [MFC], initiating drag operations
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], drop source
- OLE drag and drop [MFC], calling DoDragDrop
- drag and drop [MFC], initiating drag operations
- drag and drop [MFC], drop source
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
ms.openlocfilehash: 2aa593fa953f7a9874036d48124ae7b92d88e0a6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768645"
---
# <a name="drag-and-drop-implementing-a-drop-source"></a>Arrastrar y colocar: Implementación de un origen de colocación

En este artículo se explica cómo obtener la aplicación para proporcionar datos a una operación de arrastrar y colocar.

Implementación básica de un origen de colocación es relativamente sencilla. El primer paso es determinar qué eventos inician una operación de arrastre. Recomienda directrices de interfaz de usuario definen el inicio de una operación de arrastre como la selección de datos y un **WM_LBUTTONDOWN** eventos que se producen en un punto dentro de los datos seleccionados. Los ejemplos OLE de MFC [OCLIENT](../overview/visual-cpp-samples.md) y [HIERSVR](../overview/visual-cpp-samples.md) siga estas instrucciones.

Si la aplicación es un contenedor y los datos seleccionados están un objeto vinculado o incrustado de tipo `COleClientItem`, llame a su `DoDragDrop` función miembro. En caso contrario, construir un `COleDataSource` objeto, inicializarlo con la selección y llamar al objeto de origen de datos `DoDragDrop` función miembro. Si la aplicación es un servidor, use `COleServerItem::DoDragDrop`. Para obtener información acerca de cómo personalizar el comportamiento estándar de arrastrar y colocar, vea el artículo [arrastrar y colocar: Personalizar](../mfc/drag-and-drop-customizing.md).

Si `DoDragDrop` devuelve **DROPEFFECT_MOVE**, eliminar inmediatamente los datos de origen del documento de origen. Ningún otro tipo de valor devuelto de `DoDragDrop` no tiene ningún efecto en un origen de colocación.

Para obtener más información, consulte:

- [Implementar un destino de colocación](../mfc/drag-and-drop-implementing-a-drop-target.md)

- [Personalización de arrastrar y colocar](../mfc/drag-and-drop-customizing.md)

- [Crear y destruir objetos de datos OLE y orígenes de datos](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Manipular objetos de datos OLE y orígenes de datos](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="see-also"></a>Vea también

[Arrastrar y colocar (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop)<br/>
[COleClientItem::DoDragDrop](../mfc/reference/coleclientitem-class.md#dodragdrop)<br/>
[CView::OnDragLeave](../mfc/reference/cview-class.md#ondragleave)
