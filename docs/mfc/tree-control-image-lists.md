---
title: Listas de imágenes del Control de árbol | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef74b656cc85fbdcc29c7965b9398a5cbd2f44e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-image-lists"></a>Listas de imágenes del control de árbol
Cada elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) puede tener un par de imágenes de mapa de bits asociado con él. Las imágenes aparecerán en el lado izquierdo de la etiqueta de un elemento. Una imagen se muestra cuando se selecciona el elemento y la otra se muestra cuando el elemento no está seleccionado. Por ejemplo, un elemento puede mostrar una carpeta abierta cuando se selecciona y una carpeta cerrada cuando no está seleccionada.  
  
 Para utilizar imágenes de elemento, debe crear una lista de imágenes mediante la creación de un [CImageList](../mfc/reference/cimagelist-class.md) objeto y usando la [CImageList:: Create](../mfc/reference/cimagelist-class.md#create) función para crear la lista de imágenes asociada. A continuación, agregue los mapas de bits deseado a la lista y asociar la lista con el control de árbol mediante la [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) función miembro. De forma predeterminada, todos los elementos muestran la primera imagen en la lista de imágenes para los Estados seleccionadas y no seleccionadas. Puede cambiar el comportamiento predeterminado para un elemento determinado mediante la especificación de los índices de las imágenes seleccionadas y no seleccionadas cuando se agrega el elemento del control de árbol utilizando la [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) función miembro. Puede cambiar los índices después de agregar un elemento mediante el uso de la [función miembro SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) función miembro.  
  
 Listas de imágenes de un control de árbol también pueden contener imágenes superpuestas, que están diseñadas para que se superpongan en imágenes del elemento. Un valor distinto de cero en bits 8 al 11 del estado del elemento de control de árbol especifica el índice basado en uno de una imagen superpuesta (0 no indica ninguna imagen superpuesta). Puesto que se utiliza un índice basado en uno de 4 bits, imágenes superpuestas deben estar entre las 15 primeras imágenes en las listas de imágenes. Para obtener más información acerca de los Estados de elemento de control de árbol, vea [información general de los Estados del elemento de Control de árbol](../mfc/tree-control-item-states-overview.md) anteriormente en este tema.  
  
 Si se especifica una lista de imágenes de estado, un control de árbol reserva espacio a la izquierda del icono de cada elemento de una imagen de estado. Una aplicación puede utilizar imágenes de estado, como casillas de verificación activadas y desactivadas, para indicar los Estados de elemento definidos por la aplicación. Un valor distinto de cero en bits 12 a 15 especifica el índice basado en uno de una imagen de estado (0 no indica que no hay ninguna imagen de estado).  
  
 Mediante la especificación de la **I_IMAGECALLBACK** valor en lugar del índice de una imagen, puede retrasar la especificación de la imagen seleccionada o no hasta que el elemento está a punto de volver a dibujar. **I_IMAGECALLBACK** dirige el control de árbol para consultar la aplicación para el índice mediante el envío de la [TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) mensaje de notificación.  
  
 El [función miembro GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) función miembro recupera el identificador de la lista de imágenes de un control de árbol. Esta función es útil si necesita agregar más imágenes a la lista. Para obtener más información acerca de las listas de imágenes, vea [utilizar CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) en el *referencia de MFC*, y [listas de imágenes](http://msdn.microsoft.com/library/windows/desktop/bb761389) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

