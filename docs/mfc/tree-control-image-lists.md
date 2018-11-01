---
title: Listas de imágenes del control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 2b680ece131df434b65f02501f78f0cdb6507f08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551767"
---
# <a name="tree-control-image-lists"></a>Listas de imágenes del control de árbol

Cada elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) puede tener un par de imágenes de mapa de bits asociados con él. Las imágenes aparecen en el lado izquierdo de la etiqueta de un elemento. Una imagen se muestra cuando el elemento está seleccionado y el otro se muestra cuando el elemento no está seleccionado. Por ejemplo, un elemento podría mostrar una carpeta abierta cuando está seleccionado y una carpeta cerrada cuando no está seleccionada.

Para utilizar imágenes de elemento, debe crear una lista de imágenes mediante la creación de un [CImageList](../mfc/reference/cimagelist-class.md) objeto y el uso de la [CImageList:: Create](../mfc/reference/cimagelist-class.md#create) función para crear la lista de imágenes asociado. A continuación, agregue los mapas de bits deseado a la lista y asociar la lista con el control de árbol mediante el [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) función miembro. De forma predeterminada, todos los elementos de mostrarán la primera imagen en la lista de imágenes para los Estados seleccionados y los no seleccionados. Puede cambiar el comportamiento predeterminado para un elemento determinado mediante la especificación de los índices de las imágenes seleccionadas y no seleccionadas cuando se agrega el elemento para el control de árbol mediante el [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) función miembro. Puede cambiar los índices después de agregar un elemento mediante el uso de la [función miembro SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) función miembro.

Listas de imágenes de un control de árbol también pueden contener imágenes superpuestas, que están diseñadas para que se superpongan en imágenes del elemento. Un valor distinto de cero en bits del 8 al 11 de estado del elemento de control de árbol especifica el índice basado en uno de una imagen de superposición (0 no indica que no hay ninguna imagen de superposición). Dado que se utiliza un índice basado en uno de 4 bits, deben ser imágenes superpuestas entre las primeros 15 imágenes en las listas de imágenes. Para obtener más información acerca de los Estados de elemento de control de árbol, vea [información general de los Estados del elemento de Control de árbol](../mfc/tree-control-item-states-overview.md) anteriormente en este tema.

Si se especifica una lista de imágenes de estado, un control de árbol reserva espacio a la izquierda del icono de cada elemento de una imagen de estado. Una aplicación puede utilizar imágenes de estado, por ejemplo, casillas activados y está desactivadas para indicar estados de elemento definido por la aplicación. Un valor distinto de cero en bits del 12 al 15 especifica el índice basado en uno de una imagen de estado (0 no indica que no hay ninguna imagen de estado).

Especificando el **I_IMAGECALLBACK** valor en lugar del índice de una imagen, puede retrasar la especificación de la imagen seleccionada o no hasta que el elemento está a punto de volver a dibujar. **I_IMAGECALLBACK** dirige el control de árbol para consultar la aplicación para el índice mediante el envío de la [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) mensaje de notificación.

El [función miembro GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) función miembro recupera el identificador de la lista de imágenes de un control de árbol. Esta función es útil si necesita agregar más imágenes a la lista. Para obtener más información acerca de las listas de imágenes, consulte [utilizar CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) en el *referencia de MFC*, y [listas de imágenes](https://msdn.microsoft.com/library/windows/desktop/bb761389) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

