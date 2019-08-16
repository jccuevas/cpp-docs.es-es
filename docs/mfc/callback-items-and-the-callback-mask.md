---
title: Elementos de devolución de llamada y máscara de devolución de llamada
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 5c326d8498ea297936254a8650f666103ea3c772
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509136"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementos de devolución de llamada y máscara de devolución de llamada

Para cada uno de sus elementos, un control de vista de lista normalmente almacena el texto de la etiqueta, el índice de la lista de imágenes de los iconos del elemento y un conjunto de marcadores de bits para el estado del elemento. Puede definir elementos individuales como elementos de devolución de llamada, que resultan útiles si la aplicación ya almacena parte de la información de un elemento.

Para definir un elemento como un elemento de devolución de llamada, especifique los valores `pszText` adecuados `iImage` para los miembros `LVITEM` y de la estructura (vea [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)). Si la aplicación mantiene el texto del elemento o del subelemento, especifique el valor de **LPSTR_TEXTCALLBACK** para `pszText` el miembro. Si la aplicación realiza un seguimiento del icono del elemento, especifique el valor de **I_IMAGECALLBACK** para el `iImage` miembro.

Además de definir elementos de devolución de llamada, también puede modificar la máscara de devolución de llamada del control. Esta máscara es un conjunto de marcadores de bits que especifican los Estados del elemento para los que la aplicación, en lugar del control, almacena los datos actuales. La máscara de devolución de llamada se aplica a todos los elementos del control, a diferencia de la designación del elemento de devolución de llamada, que se aplica a un elemento específico. De forma predeterminada, la máscara de devolución de llamada es cero, lo que significa que el control realiza un seguimiento de todos los Estados de elemento. Para cambiar este comportamiento predeterminado, inicialice la máscara a cualquier combinación de los valores siguientes:

- **LVIS_CUT** El elemento está marcado para una operación de cortar y pegar.

- **LVIS_DROPHILITED** El elemento se resalta como un destino de arrastrar y colocar.

- **LVIS_FOCUSED** El elemento tiene el foco.

- **LVIS_SELECTED** El elemento está seleccionado.

- **LVIS_OVERLAYMASK** La aplicación almacena el índice de la lista de imágenes de la imagen de superposición actual para cada elemento.

- **LVIS_STATEIMAGEMASK** La aplicación almacena el índice de la lista de imágenes de la imagen de estado actual para cada elemento.

Para obtener más información sobre cómo recuperar y establecer esta máscara, vea [CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) y [CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
