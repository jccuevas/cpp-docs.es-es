---
title: Usar CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 775668426cd11e20a4c863f07a964935d0d5420f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447179"
---
# <a name="using-cspinbuttonctrl"></a>Usar CSpinButtonCtrl

El control de *botón de número* (también conocido como control *de* flechas) proporciona un par de flechas en las que un usuario puede hacer clic para ajustar un valor. Este valor se conoce como la *posición actual*. La posición permanece dentro del intervalo del botón de número. Cuando el usuario hace clic en la flecha arriba, la posición se desplaza hacia el máximo; y cuando el usuario hace clic en la flecha hacia abajo, la posición se desplaza hacia el mínimo.

La clase [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) representa el control de botón de número en MFC.

> [!NOTE]
>  De forma predeterminada, el intervalo para el botón de número tiene el valor máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba se reduce la posición y al hacer clic en la flecha hacia abajo se aumenta. Use [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) para ajustar estos valores.

Normalmente, la posición actual se muestra en un control complementario. El control complementario se conoce como la *ventana relacionada*. Para ver una ilustración de un control de botón de número, vea acerca de los [controles](/windows/win32/Controls/up-down-controls) de flechas en el Windows SDK.

Para crear un control de número y una ventana relacionada con el control de edición, en Visual Studio, arrastre primero un control de edición al cuadro de diálogo o ventana y, a continuación, arrastre un control de número. Seleccione el control de número y establezca sus propiedades **auto Buddy** y **set Buddy Integer** en **true**. Establezca también la propiedad **alignment** ; La **alineación derecha** es la más habitual. Con esta configuración, el control de edición se establece como la ventana relacionada porque precede directamente al control de edición en el orden de tabulación. El control de edición muestra enteros y el control de número se incrusta en el lado derecho del control de edición. Opcionalmente, puede establecer el intervalo válido del control de número mediante el método [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) . No es necesario que los controladores de eventos se comuniquen entre el control de número y la ventana relacionada porque intercambian datos directamente. Si usa un control de número para algún otro propósito, por ejemplo, para paginar a través de una secuencia de ventanas o cuadros de diálogo, agregue un controlador para el mensaje de UDN_DELTAPOS y realice la acción personalizada allí.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Estilos de botón de cuadro de número](../mfc/spin-button-styles.md)

- [Funciones miembro del botón de número](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Consulte también

[Controles](../mfc/controls-mfc.md)
