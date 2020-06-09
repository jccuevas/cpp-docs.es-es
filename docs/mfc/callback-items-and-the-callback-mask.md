---
title: Elementos de devolución de llamada y máscara de devolución de llamada
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 1c46f6edb44e4898c0245209ca837cd0eb716304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624969"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementos de devolución de llamada y máscara de devolución de llamada

Para cada uno de sus elementos, un control de vista de lista normalmente almacena el texto de la etiqueta, el índice de la lista de imágenes de los iconos del elemento y un conjunto de marcadores de bits para el estado del elemento. Puede definir elementos individuales como elementos de devolución de llamada, que resultan útiles si la aplicación ya almacena parte de la información de un elemento.

Para definir un elemento como un elemento de devolución de llamada, especifique los valores adecuados para los `pszText` `iImage` miembros y de la `LVITEM` estructura (vea [CListCtrl:: GetItem](reference/clistctrl-class.md#getitem)). Si la aplicación mantiene el texto del elemento o del subelemento, especifique el valor de **LPSTR_TEXTCALLBACK** para el `pszText` miembro. Si la aplicación realiza un seguimiento del icono del elemento, especifique el valor de **I_IMAGECALLBACK** para el `iImage` miembro.

Además de definir elementos de devolución de llamada, también puede modificar la máscara de devolución de llamada del control. Esta máscara es un conjunto de marcadores de bits que especifican los Estados del elemento para los que la aplicación, en lugar del control, almacena los datos actuales. La máscara de devolución de llamada se aplica a todos los elementos del control, a diferencia de la designación del elemento de devolución de llamada, que se aplica a un elemento específico. De forma predeterminada, la máscara de devolución de llamada es cero, lo que significa que el control realiza un seguimiento de todos los Estados de elemento. Para cambiar este comportamiento predeterminado, inicialice la máscara a cualquier combinación de los valores siguientes:

- **LVIS_CUT** El elemento está marcado para una operación de cortar y pegar.

- **LVIS_DROPHILITED** El elemento se resalta como un destino de arrastrar y colocar.

- **LVIS_FOCUSED** El elemento tiene el foco.

- **LVIS_SELECTED** El elemento está seleccionado.

- **LVIS_OVERLAYMASK** La aplicación almacena el índice de la lista de imágenes de la imagen de superposición actual para cada elemento.

- **LVIS_STATEIMAGEMASK** La aplicación almacena el índice de la lista de imágenes de la imagen de estado actual para cada elemento.

Para obtener más información sobre cómo recuperar y establecer esta máscara, vea [CListCtrl:: GetCallbackMask](reference/clistctrl-class.md#getcallbackmask) y [CListCtrl:: SetCallbackMask](reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
