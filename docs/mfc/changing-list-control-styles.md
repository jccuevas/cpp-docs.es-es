---
title: Cambiar los estilos de control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370812"
---
# <a name="changing-list-control-styles"></a>Cambiar los estilos de control de lista

Puede cambiar el estilo de ventana de un control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) en cualquier momento después de crearlo. Al cambiar el estilo de ventana, se cambia el tipo de vista que utiliza el control. Por ejemplo, para emular el Explorador, puede proporcionar elementos de menú o botones de barra de herramientas para cambiar el control entre diferentes vistas: vista de icono, vista de lista, etc.

Por ejemplo, cuando el usuario selecciona el elemento de menú, puede realizar una llamada a [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) para recuperar el estilo actual del control y, a continuación, llamar a [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) para restablecer el estilo. Para obtener más información, consulte Uso de controles de vista de [lista](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Los estilos disponibles se muestran en [Crear](../mfc/reference/clistctrl-class.md#create). Los estilos **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**y **LVS_REPORT** designar las cuatro vistas de control de lista.

## <a name="extended-styles"></a>Estilos extendidos

Además de los estilos estándar para un control de lista, hay otro conjunto, denominado estilos extendidos. Estos estilos, que se describen en [Estilos](/windows/win32/Controls/extended-list-view-styles) de vista de lista extendida en el Windows SDK, proporcionan una variedad de características útiles que personalizan el comportamiento del control de lista. Para implementar el comportamiento de un estilo determinado (por ejemplo, la selección de desplazamiento), realice una llamada a [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), pasando el estilo necesario. En el ejemplo siguiente se muestra la llamada de función:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Para que la selección de desplazamiento funcione, también debe tener **LVS_EX_ONECLICKACTIVATE** o **LVS_EX_TWOCLICKACTIVATE** activado.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
