---
title: Desactivar la opción Activar cuando esté visible
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: 42dbec7a55085235e43fa14ab6406bfb3526afdb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464836"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Desactivar la opción Activar cuando esté visible

Un control tiene dos estados básicos: activo e inactivo. Tradicionalmente, se distinguían por el hecho de que el control tuviera o no una ventana. Un control activo tenía una ventana; un control inactivo no la tenía. Con la introducción de la activación sin ventana, esta distinción ya no es universal, pero sigue aplicándose a muchos controles.

En comparación con el resto de la inicialización suele realizada un control ActiveX, la creación de una ventana es una operación muy costosa. Idealmente, un control desea aplazar la creación de su ventana hasta que sea absolutamente necesario.

Muchos controles no es necesario para que estén activos son visibles en un contenedor de todo el tiempo. A menudo, un control puede permanecer en el estado inactivo hasta que el usuario realiza una operación que requiere para activarse (por ejemplo, haciendo clic con el mouse o presionar la tecla TAB). Para hacer que un control permanezca inactivo hasta que el contenedor debe activarlo, quite el **OLEMISC_ACTIVATEWHENVISIBLE** marca de indicadores varios del control:

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

El **OLEMISC_ACTIVATEWHENVISIBLE** marca automáticamente se omite si desactiva la **activar cuando está Visible** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página de ActiveX de MFC Asistente para controles cuando se crea el control.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

