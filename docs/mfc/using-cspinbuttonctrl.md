---
title: Usar CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366481"
---
# <a name="using-cspinbuttonctrl"></a>Usar CSpinButtonCtrl

El control de *botón de giro* (también conocido como control *descendente)* proporciona un par de flechas en las que un usuario puede hacer clic para ajustar un valor. Este valor se conoce como la *posición actual.* La posición permanece dentro del rango del botón de giro. Cuando el usuario hace clic en la flecha hacia arriba, la posición se mueve hacia el máximo; y cuando el usuario hace clic en la flecha hacia abajo, la posición se mueve hacia el mínimo.

El control de botón de giro se representa en MFC mediante la [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) clase.

> [!NOTE]
> De forma predeterminada, el rango para el botón de giro tiene el máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba se reduce la posición y al hacer clic en la flecha hacia abajo se aumenta. Utilice [CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) para ajustar estos valores.

Normalmente, la posición actual se muestra en un control complementario. El control complementario se conoce como la *ventana de compañero*. Para obtener una ilustración de un control de botón de giro, consulte Acerca de los [controles descendentes](/windows/win32/Controls/up-down-controls) en el Windows SDK.

Para crear un control de giro y una ventana de compañero de control de edición, en Visual Studio, arrastre primero un control de edición al cuadro de diálogo o ventana y, a continuación, arrastre un control de giro. Seleccione el control de giro y establezca sus propiedades **Auto Buddy** y **Set Buddy Integer** en **True**. Establezca también la propiedad **Alignment;** **Alinear a** la derecha es lo más típico. Con esta configuración, el control de edición se establece como la ventana de compañero porque precede directamente al control de edición en el orden de tabulación. El control de edición muestra enteros y el control de giro está incrustado en el lado derecho del control de edición. Opcionalmente, puede establecer el intervalo válido del control spin mediante el [método CSpinButtonCtrl::SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) . No se requiere que los controladores de eventos se comuniquen entre el control de giro y la ventana de compañero porque intercambian datos directamente. Si usa un control de giro para algún otro propósito, por ejemplo, para paginar a través de una secuencia de ventanas o cuadros de diálogo, a continuación, agregue un controlador para el UDN_DELTAPOS mensaje y realizar la acción personalizada allí.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Estilos de botón de cuadro de número](../mfc/spin-button-styles.md)

- [Funciones miembro del botón de número](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Consulte también

[Controles](../mfc/controls-mfc.md)
