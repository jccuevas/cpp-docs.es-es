---
title: 'Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 94ad6e8356b5dab54ae97dbdd90812039d1425c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322061"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX

Si no ha biliado la compatibilidad con controles ActiveX al usar el Asistente para aplicaciones MFC para generar la aplicación, tendrá que agregar esta compatibilidad manualmente. En este artículo se describe el proceso para agregar manualmente la contención de controles ActiveX a una aplicación contenedora OLE existente. Si sabe de antemano que desea compatibilidad con controles ActiveX en el contenedor OLE, vea el artículo Creación de un contenedor de [controles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

> [!NOTE]
> En este artículo se usa un proyecto de contenedor de control ActiveX basado en cuadros de diálogo denominado Container y un control incrustado denominado Circ como ejemplos en los procedimientos y el código.

Para admitir controles ActiveX, debe agregar una línea de código a dos de los archivos del proyecto.

- Modifique la función `InitInstance` del cuadro de diálogo principal (que se encuentra en CONTAINER. CPP) por el Asistente para aplicaciones MFC realizando una llamada a [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), como en el ejemplo siguiente:

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Agregue lo siguiente al STDAFX del proyecto. Archivo de encabezado H:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Después de completar estos pasos, vuelva a generar el proyecto haciendo clic en **Compilar** en el menú **Generar.**

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
