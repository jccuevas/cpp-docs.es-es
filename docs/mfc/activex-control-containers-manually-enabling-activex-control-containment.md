---
title: "Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf1ba1273a349f685b70fec6706b566c2b618f23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>Contenedores de controles ActiveX: Habilitar manualmente la contención de controles ActiveX
Si no habilitó la compatibilidad con el control ActiveX cuando se usa el Asistente para aplicaciones MFC para generar la aplicación, tendrá que agregar esta compatibilidad manualmente. En este artículo se describe el proceso para agregar manualmente la contención de controles ActiveX a una aplicación existente de contenedor OLE. Si sabe de antemano que desea compatibilidad con controles ActiveX en el contenedor OLE, vea el artículo [crear un contenedor de controles ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
> [!NOTE]
>  Este artículo utiliza un basada en cuadros de diálogo contenedor proyecto de control ActiveX denominado Container y un control incrustado denominado Circ como ejemplos en los procedimientos y el código.  
  
 Para admitir controles ActiveX, debe agregar una línea de código a dos de los archivos del proyecto.  
  
-   Modificar el cuadro de diálogo principal `InitInstance` función (que se encuentra en el contenedor. CPP) mediante el Asistente para aplicaciones de MFC que realiza una llamada a [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer), como en el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   Agregue lo siguiente a STDAFX su proyecto. Archivo de encabezado de H:  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 Después de completar estos pasos, recompile el proyecto, haga clic en **generar** en el **generar** menú.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

