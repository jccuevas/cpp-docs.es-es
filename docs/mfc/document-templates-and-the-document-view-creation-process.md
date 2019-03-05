---
title: Las plantillas de documento y el proceso de creación de documentos y vistas
ms.date: 11/19/2018
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
ms.openlocfilehash: 79d24ef4b6687bce61295a92cdb90f4ce4a0d619
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290007"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Plantillas de documento y el proceso de creación de documentos y vistas

Para administrar el complejo proceso de creación de documentos con sus vistas asociadas y las ventanas de marco, el marco de trabajo usa dos clases de plantilla de documento: [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) para las aplicaciones SDI y [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para aplicaciones MDI. Un `CSingleDocTemplate` puede crear y guardar un documento de un tipo a la vez. Un `CMultiDocTemplate` mantiene una lista de muchos documentos abiertos de un tipo.

Algunas aplicaciones admiten varios tipos de documentos. Por ejemplo, una aplicación podría admitir documentos de texto y gráficos. En este tipo de aplicación, cuando el usuario elige el comando nuevo en el menú archivo, un cuadro de diálogo muestra una lista de posibles tipos de documento de nuevo para abrir. Para cada tipo de documento admitidos, la aplicación utiliza un objeto de plantilla de documento distinto. La ilustración siguiente muestra la configuración de una aplicación MDI que admite dos tipos de documento y presenta varios documentos abiertos.

![Aplicación MDI con dos tipos de documentos](../mfc/media/vc387h1.gif "aplicación MDI con dos tipos de documentos") <br/>
Una aplicación MDI con dos tipos de documentos

Las plantillas de documento se crean y mantienen por el objeto de aplicación. Una de las tareas principales realizadas durante la aplicación `InitInstance` función consiste en crear una o varias plantillas de documento del tipo adecuado. Esta característica se describe en [creación de plantillas de documento](../mfc/document-template-creation.md). El objeto de aplicación almacena un puntero a cada plantilla de documento en su lista de plantillas y proporciona una interfaz para agregar plantillas de documento.

Si necesita admitir dos o más tipos de documento, debe agregar una llamada adicional al [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) para cada tipo de documento.

Se registra un icono para cada plantilla de documento según su posición en la lista de la aplicación de plantillas de documento. El orden de las plantillas de documento viene determinada por el orden en que se agregan con llamadas a `AddDocTemplate`. MFC se da por supuesto que el primer recurso de icono en la aplicación es el icono de aplicación, el siguiente recurso de icono es el primer icono de documento y así sucesivamente.

Por ejemplo, una plantilla de documento es el tercero de tres para la aplicación. Si hay un recurso de icono en la aplicación en el índice 3, ese icono se utiliza para la plantilla de documento. Si no es así, se utiliza el icono en el índice 0 de forma predeterminada.

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[Creación de plantillas de documentos](../mfc/document-template-creation.md)<br/>
[Crear documentos y vistas](../mfc/document-view-creation.md)<br/>
[Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)
