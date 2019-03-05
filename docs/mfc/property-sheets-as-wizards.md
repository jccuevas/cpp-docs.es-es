---
title: Hojas de propiedades como asistentes
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
ms.openlocfilehash: c60148c099b34993bef0c9808e6561e37c26cc7f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301680"
---
# <a name="property-sheets-as-wizards"></a>Hojas de propiedades como asistentes

Una característica clave de una hoja de propiedades del asistente es que la navegación se proporciona con los botones siguiente o finalizar, Atrás y Cancelar en lugar de pestañas. Se debe llamar a [CPropertySheet:: SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) antes de llamar a [CPropertySheet:: DoModal](../mfc/reference/cpropertysheet-class.md#domodal) en el objeto de hoja de propiedades para aprovechar esta característica.

El usuario recibe el mismo [notificaciones CPropertyPage:: OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) y [CPropertyPage:: OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) notificaciones mientras se desplaza de una página a otra página. Botones siguiente y finalizar son controles mutuamente excluyentes; es decir, solo uno de ellos se mostrarán a la vez. En la primera página, debe estar habilitado el botón siguiente. Si el usuario está en la última página, debe habilitarse el botón Finalizar. No Esto se realiza automáticamente el marco de trabajo. Se debe llamar a [CPropertySheet:: SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) en la última página para lograr esto.

Para mostrar todos los botones de forma predeterminada, debe mostrar el botón Finalizar y mueva el botón siguiente. A continuación, mueva el botón Atrás para que se mantiene su posición relativa en el botón siguiente.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>Vea también

[Hojas de propiedades](../mfc/property-sheets-mfc.md)
