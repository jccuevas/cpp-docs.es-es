---
title: 'Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fc9b97e47b64f9f4d60bf45afe9628b11c657c8
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204683"
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

