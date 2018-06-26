---
title: Creación de la vista de documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 894bb5a0b3a4c86d764fc6f4a0e4b9ae18422669
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931858"
---
# <a name="documentview-creation"></a>Crear documentos y vistas
El marco de trabajo proporciona implementaciones de la **New** y **abiertos** comandos (entre otras cosas) en el **archivo** menú. Creación de un nuevo documento y su vista asociada y la ventana de marco es un esfuerzo cooperativo entre el objeto de aplicación, una plantilla de documento, el documento recién creado y la ventana de marco recién creada. La tabla siguiente resume qué objetos crean qué.  
  
### <a name="object-creators"></a>Creadores de objetos  
  
|Creator|Crea|  
|-------------|-------------|  
|Application (objeto)|Plantilla de documento|  
|Plantilla de documento|Documento|  
|Plantilla de documento|Ventana de marco|  
|Ventana de marco|Ver|  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Creación de la plantilla de documento](../mfc/document-template-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)   
 [Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

