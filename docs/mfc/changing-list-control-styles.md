---
title: Cambiar los estilos de control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: e515f56f00aa45a14c24bcd635770e803f7f8e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615984"
---
# <a name="changing-list-control-styles"></a>Cambiar los estilos de control de lista

Puede cambiar el estilo de ventana de un control de lista ([CListCtrl](reference/clistctrl-class.md)) en cualquier momento después de crearlo. Al cambiar el estilo de ventana, cambia el tipo de vista que utiliza el control. Por ejemplo, para emular el explorador, puede proporcionar elementos de menú o botones de la barra de herramientas para cambiar el control entre diferentes vistas: vista de iconos, vista de lista, etc.

Por ejemplo, cuando el usuario selecciona el elemento de menú, puede llamar a [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) para recuperar el estilo actual del control y, a continuación, llamar a [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) para restablecer el estilo. Para obtener más información, vea [usar controles de vista de lista](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Los estilos disponibles se enumeran en [crear](reference/clistctrl-class.md#create). Los estilos **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**y **LVS_REPORT** designan las cuatro vistas de control de lista.

## <a name="extended-styles"></a>Estilos extendidos

Además de los estilos estándar de un control de lista, hay otro conjunto, denominado estilos extendidos. Estos estilos, descritos en los [estilos extendidos](/windows/win32/Controls/extended-list-view-styles) de la vista de lista del Windows SDK, proporcionan una variedad de características útiles que personalizan el comportamiento del control de lista. Para implementar el comportamiento de un estilo determinado (por ejemplo, al mantener el mouse en la selección), realice una llamada a [CListCtrl:: SetExtendedStyle](reference/clistctrl-class.md#setextendedstyle), pasando el estilo necesario. En el ejemplo siguiente se muestra la llamada a la función:

[!code-cpp[NVC_MFCControlLadenDialog#22](codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Para que la selección del mouse funcione, también debe tener **LVS_EX_ONECLICKACTIVATE** o **LVS_EX_TWOCLICKACTIVATE** activado.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
