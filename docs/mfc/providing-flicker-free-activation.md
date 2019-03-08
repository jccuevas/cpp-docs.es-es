---
title: Proporcionar activación sin parpadeo
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: fad24d6201260e87ff32436752a9fbf035e822ae
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287679"
---
# <a name="providing-flicker-free-activation"></a>Proporcionar activación sin parpadeo

Si el control se dibuja de forma idéntica en los Estados inactivos y activos (y no utiliza activación sin ventana), puede eliminar las operaciones de dibujo y el parpadeo visual que se suelen producir al realizar la transición entre los inactivos Estados y activo. Para ello, incluya el **noFlickerActivate** marca en el conjunto de indicadores devueltos por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

El código para incluir esta marca se genera automáticamente si selecciona la **activación sin parpadeo** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página al crear el control con el Asistente para controles de ActiveX de MFC.

Si usas la activación sin ventana, esta optimización no tiene ningún efecto.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)
