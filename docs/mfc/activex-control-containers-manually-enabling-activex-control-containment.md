---
title: 'Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: a8092a77020695163ce4fbacf7eeea2650ae9f86
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625114"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX

Si no ha habilitado la compatibilidad con controles ActiveX cuando utilizó el Asistente para aplicaciones MFC para generar la aplicación, tendrá que agregar esta compatibilidad manualmente. En este artículo se describe el proceso para agregar manualmente la contención de controles ActiveX a una aplicación contenedora OLE existente. Si sabe de antemano que desea la compatibilidad con controles ActiveX en el contenedor OLE, vea el artículo [crear un contenedor de controles ActiveX MFC](reference/creating-an-mfc-activex-control-container.md).

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

> [!NOTE]
> En este artículo se usa un proyecto de contenedor de controles ActiveX basado en cuadros de diálogo denominado contenedor y un control incrustado denominado Circ como ejemplos en los procedimientos y el código.

Para admitir controles ActiveX, debe agregar una línea de código a dos de los archivos del proyecto.

- Modifique la función del cuadro de diálogo principal `InitInstance` (se encuentra en el contenedor. CPP) mediante el Asistente para aplicaciones MFC que realiza una llamada a [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), como en el ejemplo siguiente:

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- Agregue lo siguiente al STDAFX del proyecto. Archivo de encabezado H:

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

Después de completar estos pasos, vuelva a generar el proyecto haciendo clic en **compilar** en el menú **compilar** .

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](activex-control-containers.md)
