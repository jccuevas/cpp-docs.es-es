---
title: Usar un control de animación
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], animation
- CAnimateCtrl class [MFC], animation controls
- animation controls [MFC]
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
ms.openlocfilehash: fa5ce6cc30d4bc31dbe52c0e559ce97e40acacba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631002"
---
# <a name="using-an-animation-control"></a>Usar un control de animación

Uso típico de un control de animación sigue el patrón siguiente:

- Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo, creación es automática cuando se crea el cuadro de diálogo. (Debe tener un [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) miembro en la clase de cuadro de diálogo que se corresponde con el control de animación.) Como alternativa, puede usar el [crear](../mfc/reference/canimatectrl-class.md#create) función miembro para crear el control como una ventana secundaria de cualquier ventana.

- Cargar un clip AVI en el control de animación mediante una llamada a la [abierto](../mfc/reference/canimatectrl-class.md#open) función miembro. Si el control de animación está en un cuadro de diálogo, es un buen lugar para hacer esto en la clase de cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) función.

- Reproduzca la secuencia mediante una llamada a la [reproducir](../mfc/reference/canimatectrl-class.md#play) función miembro. Si el control de animación está en un cuadro de diálogo, es un buen lugar para hacer esto en la clase de cuadro de diálogo `OnInitDialog` función. Una llamada a `Play` no es necesario si el control de animación tiene el estilo ACS_AUTOPLAY establecida.

- Si desea mostrar las partes del clip o reproducirlo fotograma a fotograma, utilice el `Seek` función miembro. Para detener un clip que reproduce, use el `Stop` función miembro.

- Si no va a destruir el control inmediatamente, quite el clip de la memoria mediante una llamada a la `Close` función miembro.

- Si el control de animación está en un cuadro de diálogo y el `CAnimateCtrl` automáticamente se destruirá el objeto. Si no, deberá asegurarse de que el control y la `CAnimateCtrl` objeto se destruyan correctamente. Cierra el clip AVI destruir el control automáticamente.

## <a name="see-also"></a>Vea también

[Uso de CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

