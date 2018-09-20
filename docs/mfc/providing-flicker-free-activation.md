---
title: Proporcionar activación sin parpadeo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd9f780472b8256f6d8332ecbde08138d85c8ebd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378332"
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

