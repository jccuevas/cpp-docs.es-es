---
title: Configuración del control de progreso
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 1960b15c2f76d7cbfc9f249a77481b795e6a27ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307684"
---
# <a name="settings-for-the-progress-control"></a>Configuración del control de progreso

La configuración básica para el control de progreso ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) es el intervalo y la posición actual. El intervalo representa toda la duración de la operación. La posición actual representa el progreso que la aplicación se ha realizado para completar la operación. Los cambios realizados en el intervalo o la posición que el control de progreso para actualizarse a sí mismo.

De forma predeterminada, se establece el intervalo 0 - 100 y la posición inicial se establece en 0. Para recuperar los valores del intervalo actual del control de progreso, utilice el [GetRange](../mfc/reference/cprogressctrl-class.md#getrange) función miembro. Para cambiar el intervalo, utilice el [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) función miembro.

Para establecer la posición, utilice [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Para recuperar la posición actual sin especificar un valor nuevo, use [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Por ejemplo, puede simplemente consultar el estado de la operación actual.

Para avanzar la posición actual del control de progreso, utilice [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Para establecer la cantidad de cada paso, utilice [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>Vea también

[Uso de CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
