---
title: Estilos para el control de progreso
ms.date: 11/19/2018
helpviewer_keywords:
- PBS_SMOOTH style
- progress controls [MFC], styles
- PBS_VERTICAL style
- CProgressCtrl class [MFC], styles
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
ms.openlocfilehash: 5d33e9306c1d70bb58ad628297360bc6e34e6ce2
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52174959"
---
# <a name="styles-for-the-progress-control"></a>Estilos para el control de progreso

Cuando se crea inicialmente el control de progreso ([CProgressCtrl::Create](../mfc/reference/cprogressctrl-class.md#create)), use el *dwStyle* parámetro para especificar los estilos de ventana que desee para el control de progreso. La siguiente lista detalla los estilos de ventana aplicables. El control pasa por alto cualquier estilo de ventana que no sea de los mencionados aquí. Siempre debe crear el control como una ventana secundaria, normalmente de un elemento primario de cuadro de diálogo.

|Estilo de ventana|Efecto|
|------------------|------------|
|WS_BORDER|Crea un borde alrededor de la ventana.|
|WS_CHILD|Crea una ventana secundaria (siempre se debe usar para `CProgressCtrl`).|
|WS_CLIPCHILDREN|Excluye el área ocupada por ventanas secundarias cuando se dibuja en la ventana primaria. Se usa al crear la ventana primaria.|
|WS_CLIPSIBLINGS|Recorta las ventanas secundarias relacionados entre sí.|
|WS_DISABLED|Crea una ventana que está deshabilitada inicialmente.|
|WS_VISIBLE|Crea una ventana que está visible inicialmente.|
|WS_TABSTOP|Especifica que el control puede recibir el foco cuando el usuario presiona la tecla TAB para desplazarse a ella.|

Además, puede especificar dos estilos que se aplican solo al control de progreso, PBS_VERTICAL y PBS_SMOOTH.

Utilice PBS_VERTICAL para orientar el control verticalmente, en lugar de horizontalmente. Utilice PBS_SMOOTH para rellenar el control completo, en lugar de mostrar pequeños cuadrados delineados que rellenar el control de forma incremental.

Sin PBS_SMOOTH (estilo):

![Estilo de barra de progreso estándar](../mfc/media/vc4ruw1.gif "estilo de barra de progreso estándar")

Con los estilos PBS_SMOOTH y PBS_VERTICAL:

![Estilo suave y vertical de la barra de progreso](../mfc/media/vc4ruw2.gif "estilo suave y vertical de la barra de progreso")

Para obtener más información, consulte [estilos de ventana](../mfc/reference/styles-used-by-mfc.md#frame-window-styles-mfc) en el *referencia de MFC*.

## <a name="see-also"></a>Vea también

[Uso de CProgressCtrl](../mfc/using-cprogressctrl.md)

