---
title: Plantillas de documento y el proceso de creación de vista de documentos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2d8308e69cf53db4be51f6ce742df41edaa89ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348096"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Plantillas de documento y el proceso de creación de documentos y vistas
Para administrar el complejo proceso de creación de documentos con sus vistas asociadas y las ventanas de marco, el marco de trabajo utiliza dos clases de plantilla de documento: [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) para aplicaciones SDI y [CMultiDocTemplate ](../mfc/reference/cmultidoctemplate-class.md) para las aplicaciones MDI. Un `CSingleDocTemplate` puede crear y almacenar un documento de un tipo a la vez. Un `CMultiDocTemplate` mantiene una lista de muchos documentos abiertos de un tipo.  
  
 Algunas aplicaciones admiten varios tipos de documentos. Por ejemplo, una aplicación podría admitir documentos de texto y gráficos. En este tipo de aplicación, cuando el usuario elige el comando nuevo en el menú archivo, un cuadro de diálogo muestra una lista de posibles tipos de documento de nuevo para abrir. Para cada tipo de documento admitidos, la aplicación utiliza un objeto de plantilla de documento distintos. En la siguiente ilustración muestra la configuración de una aplicación MDI que admite dos tipos de documento y presenta varios documentos abiertos.  
  
 ![Aplicación MDI con dos tipos de documentos](../mfc/media/vc387h1.gif "vc387h1")  
Una aplicación MDI con dos tipos de documentos  
  
 Plantillas de documento se crean y mantienen por el objeto application. Una de las tareas principales realizadas durante la aplicación `InitInstance` función consiste en crear una o varias plantillas de documento del tipo adecuado. Esta característica se describe en [creación de la plantilla de documento](../mfc/document-template-creation.md). El objeto de aplicación almacena un puntero a cada plantilla de documento en su lista de plantillas y proporciona una interfaz para agregar plantillas de documento.  
  
 Si necesita admitir dos o más tipos de documento, debe agregar una llamada adicional al [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) para cada tipo de documento.  
  
 Se registra un icono para cada plantilla de documento en función de su posición en lista la aplicación de plantillas de documento. El orden de las plantillas de documento se determina por el orden en que se agregan mediante llamadas a `AddDocTemplate`. MFC se da por supuesto que el primer recurso de icono de la aplicación es el icono de la aplicación, el siguiente recurso de icono es el primer icono de documento y así sucesivamente.  
  
 Por ejemplo, una plantilla de documento es el tercero de tres iconos de la aplicación. Si hay un recurso de icono en la aplicación en el índice 3, se usa ese icono para la plantilla de documento. Si no es así, el icono en el índice 0 se utiliza como valor predeterminado.  
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [Creación de la plantilla de documento](../mfc/document-template-creation.md)   
 [Creación de documento/vista](../mfc/document-view-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)   
 [Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

