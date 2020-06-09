---
title: Plantillas de documento y el proceso de creación de documentos y vistas
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
ms.openlocfilehash: b96a11926927e89890ca268dcff7d347079b25fb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615777"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Plantillas de documento y el proceso de creación de documentos y vistas

Para administrar el proceso complejo de creación de documentos con sus vistas y ventanas de marco asociadas, el marco de trabajo usa dos clases de plantilla de documento: [CSingleDocTemplate](reference/csingledoctemplate-class.md) para aplicaciones SDI y [CMULTIDOCTEMPLATE](reference/cmultidoctemplate-class.md) para aplicaciones MDI. `CSingleDocTemplate`Puede crear y almacenar un documento de un tipo cada vez. Un `CMultiDocTemplate` mantiene una lista de muchos documentos abiertos de un tipo.

Algunas aplicaciones admiten varios tipos de documentos. Por ejemplo, una aplicación puede admitir documentos de texto y documentos de gráficos. En este tipo de aplicación, cuando el usuario elige el comando nuevo en el menú Archivo, un cuadro de diálogo muestra una lista de posibles tipos de documento nuevos para abrir. Para cada tipo de documento admitido, la aplicación usa un objeto de plantilla de documento distinto. En la ilustración siguiente se muestra la configuración de una aplicación MDI que admite dos tipos de documentos y muestra varios documentos abiertos.

![Aplicación MDI con dos tipos de documentos](../mfc/media/vc387h1.gif "Aplicación MDI con dos tipos de documentos") <br/>
Una aplicación MDI con dos tipos de documentos

El objeto de aplicación crea y mantiene las plantillas de documento. Una de las tareas clave realizadas durante la función de la aplicación `InitInstance` es construir una o varias plantillas de documento del tipo adecuado. Esta característica se describe en [creación de plantillas de documentos](document-template-creation.md). El objeto Application almacena un puntero a cada plantilla de documento en su lista de plantillas y proporciona una interfaz para agregar plantillas de documento.

Si necesita admitir dos o más tipos de documento, debe agregar una llamada adicional a [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate) para cada tipo de documento.

Se registra un icono para cada plantilla de documento en función de su posición en la lista de plantillas de documentos de la aplicación. El orden de las plantillas de documento viene determinado por el orden en que se agregan con llamadas a `AddDocTemplate` . MFC supone que el primer recurso de icono de la aplicación es el icono de la aplicación, el recurso de icono siguiente es el primer icono de documento, y así sucesivamente.

Por ejemplo, una plantilla de documento es la tercera de tres para la aplicación. Si hay un recurso de icono en la aplicación en el índice 3, ese icono se usa para la plantilla de documento. En caso contrario, se usa el icono del índice 0 como valor predeterminado.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](general-mfc-topics.md)<br/>
[Creación de plantillas de documentos](document-template-creation.md)<br/>
[Crear documentos y vistas](document-view-creation.md)<br/>
[Relaciones entre objetos MFC](relationships-among-mfc-objects.md)<br/>
[Crear nuevos documentos, ventanas y vistas](creating-new-documents-windows-and-views.md)
