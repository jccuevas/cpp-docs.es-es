---
title: Cambiar los estilos de control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 2ba9ae81f7b1693be0df3565256a65e4e3561fd3
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344464"
---
# <a name="changing-list-control-styles"></a>Cambiar los estilos de control de lista

Puede cambiar el estilo de ventana de un control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) en cualquier momento después de crearlo. Al cambiar el estilo de ventana, cambie el tipo de vista que usa el control. Por ejemplo, para emular el explorador, puede proporcionar elementos de menú o botones de barra de herramientas para cambiar el control entre distintas vistas: vista de iconos, vista de lista y así sucesivamente.

Por ejemplo, cuando el usuario selecciona el elemento de menú, puede realizar una llamada a [GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga) para recuperar el estilo actual del control y, a continuación, llamar a [SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) para restablecer el estilo. Para obtener más información, consulte [mediante controles de vista de lista](/windows/desktop/Controls/using-list-view-controls) en el SDK de Windows.

Estilos disponibles se enumeran en [crear](../mfc/reference/clistctrl-class.md#create). Los estilos **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**, y **LVS_REPORT** designar las vistas de control de lista de cuatro.

## <a name="extended-styles"></a>Estilos extendidos

Además de los estilos estándares para un control de lista, hay otro conjunto, que se conoce como estilos extendidos. Estos estilos, descritos en [estilos extendidos de vista de lista](/windows/desktop/Controls/extended-list-view-styles) en el SDK de Windows, ofrecen una variedad de características útiles que personalizan el comportamiento del control de lista. Para implementar el comportamiento de un estilo determinado (por ejemplo, la selección al mantener el mouse), realice una llamada a [CListCtrl:: SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), pasa el estilo necesario. El ejemplo siguiente muestra la llamada de función:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Para que funcione la selección al mantener el mouse, también debe tener una **LVS_EX_ONECLICKACTIVATE** o **LVS_EX_TWOCLICKACTIVATE** activado.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
