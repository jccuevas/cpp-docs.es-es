---
title: "Contenedores de controles ActiveX: Habilitar manualmente la contenci&#243;n de controles ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++], habilitar"
  - "controles ActiveX [C++], habilitar contenedores"
  - "AfxEnableControlContainer (método)"
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Contenedores de controles ActiveX: Habilitar manualmente la contenci&#243;n de controles ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si no habilitó el control ActiveX admite cuando se utiliza el asistente para generar la aplicación, tendrá que agregar esta compatibilidad manualmente.  En este artículo se describe el proceso para agregar manualmente la contención de controles ActiveX a una aplicación contenedora OLE existente.  Si sabe de antemano que desea compatibilidad con controles ActiveX en el contenedor OLE, vea el artículo [Crear un contenedor de controles ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
> [!NOTE]
>  Este artículo utiliza un contenedor diálogo\- basado en proyecto denominado de contenedor de controles ActiveX y un control incrustado denominados Circ como ejemplos en los procedimientos y el código.  
  
 Para admitir los controles ActiveX, debe agregar una línea de código a dos de los archivos de proyecto.  
  
-   Modifique la función de `InitInstance` de diálogo principal \(encontrada en CONTAINER.CPP\) por el asistente para aplicaciones MFC que crea una llamada a [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md), como en el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]  
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]  
  
-   Agregue el siguiente al archivo de encabezado de STDAFX.H de proyecto:  
  
     [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/CPP/activex-control-containers-manually-enabling-activex-control-containment_3.h)]  
  
 Después de completar estos pasos, recompile el proyecto haciendo clic **Compilación** en el menú de **Compilación** .  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)