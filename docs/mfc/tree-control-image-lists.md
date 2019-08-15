---
title: Listas de imágenes del control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: 8f9e323244657ea6a7cc132deab6deedfcd1a167
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513360"
---
# <a name="tree-control-image-lists"></a>Listas de imágenes del control de árbol

Cada elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) puede tener un par de imágenes de mapa de columnas asociadas. Las imágenes aparecen en el lado izquierdo de la etiqueta de un elemento. Cuando el elemento está seleccionado, se muestra una imagen y la otra se muestra cuando no se selecciona el elemento. Por ejemplo, un elemento podría mostrar una carpeta abierta cuando se selecciona y una carpeta cerrada cuando no está seleccionada.

Para usar imágenes de elementos, debe crear una lista de imágenes mediante la construcción de un objeto [CImageList](../mfc/reference/cimagelist-class.md) y el uso de la función [CImageList:: Create](../mfc/reference/cimagelist-class.md#create) para crear la lista de imágenes asociada. A continuación, agregue los mapas de bits que desee a la lista y asocie la lista con el control de árbol mediante la función miembro [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) . De forma predeterminada, todos los elementos muestran la primera imagen de la lista de imágenes tanto para los Estados seleccionados como para los no seleccionados. Puede cambiar el comportamiento predeterminado de un elemento determinado especificando los índices de las imágenes seleccionadas y no seleccionadas al agregar el elemento al control de árbol mediante la función miembro [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Puede cambiar los índices después de agregar un elemento mediante la función miembro [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) .

Las listas de imágenes de un control de árbol también pueden contener imágenes superpuestas, que están diseñadas para superponerse en imágenes de elementos. Un valor distinto de cero en los bits 8 a 11 del estado de un elemento de control de árbol especifica el índice de base uno de una imagen de superposición (0 indica que no hay ninguna imagen superpuesta). Dado que se usa un índice basado en uno de 4 bits, las imágenes superpuestas deben encontrarse entre las primeras 15 imágenes de las listas de imágenes. Para obtener más información sobre los Estados de los elementos de control de árbol, vea [información general sobre los Estados de los elementos de control de árbol](../mfc/tree-control-item-states-overview.md) anteriormente en este tema.

Si se especifica una lista de imágenes de estado, un control de árbol Reserva espacio a la izquierda del icono de cada elemento para una imagen de estado. Una aplicación puede usar imágenes de estado, como casillas comprobadas y desactivadas, para indicar los Estados de los elementos definidos por la aplicación. Un valor distinto de cero en los bits 12 a 15 especifica el índice de base uno de una imagen de estado (0 indica que no hay ninguna imagen de estado).

Al especificar el valor de **I_IMAGECALLBACK** en lugar del índice de una imagen, puede retrasar la especificación de la imagen seleccionada o no seleccionada hasta que se vuelva a dibujar el elemento. **I_IMAGECALLBACK** dirige el control de árbol para consultar el índice en la aplicación enviando el mensaje de notificación [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) .

La función miembro [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) recupera el identificador de la lista de imágenes de un control de árbol. Esta función es útil si necesita agregar más imágenes a la lista. Para obtener más información sobre las listas de imágenes, vea [usar CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) en la *referencia de MFC*y [listas de imágenes](/windows/win32/controls/image-lists) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
