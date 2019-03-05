---
title: 'Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 80ca25192f3dbda711b0398917cfa68571cd2c55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302733"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX

Si no habilitó la compatibilidad con el control ActiveX cuando se usa el Asistente para aplicaciones MFC para generar la aplicación, tendrá que agregar manualmente esta compatibilidad. En este artículo se describe el proceso para agregar manualmente la contención de controles ActiveX a una aplicación existente de contenedor OLE. Si conoce de antemano que desea compatibilidad con controles ActiveX en el contenedor OLE, vea el artículo [crear un contenedor de controles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

> [!NOTE]
>  Este artículo usa un basada en el cuadro de diálogo ActiveX control contenedor proyecto denominado contenedor y un control incrustado denominado Circ como ejemplos en los procedimientos y código.

Para admitir controles ActiveX, debe agregar una línea de código a dos de los archivos del proyecto.

- Modificar el cuadro de diálogo principal `InitInstance` función (que se encuentra en el contenedor. (CPP) mediante una llamada a MFC Application Wizard [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), como en el ejemplo siguiente:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Agregue lo siguiente a STDAFX su proyecto. Archivo de encabezado H:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Después de haber completado estos pasos, vuelva a generar el proyecto haciendo **compilar** en el **compilar** menú.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
