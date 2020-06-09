---
title: Clear plantillas de documentos
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 952a383792eb3a4d0a4ed1b3e24dd82f7fa644cf
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615783"
---
# <a name="document-template-creation"></a>Clear plantillas de documentos

Al crear un nuevo documento como respuesta a un comando **nuevo** o **abrir** desde el menú **archivo** , la plantilla de documento también crea una nueva ventana de marco a través de la cual se puede ver el documento.

El constructor Document-template especifica qué tipos de documentos, ventanas y vistas podrá crear la plantilla. Esto viene determinado por los argumentos que se pasan al constructor Document-template. En el código siguiente se muestra la creación de un [CMultiDocTemplate](reference/cmultidoctemplate-class.md) para una aplicación de ejemplo:

[!code-cpp[NVC_MFCDocView#7](codesnippet/cpp/document-template-creation_1.cpp)]

El puntero a un nuevo `CMultiDocTemplate` objeto se utiliza como argumento para [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate). Los argumentos para el `CMultiDocTemplate` constructor incluyen el identificador de recurso asociado a los menús y aceleradores del tipo de documento, y tres usos de la macro [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) . `RUNTIME_CLASS`Devuelve el objeto [CRuntimeClass](reference/cruntimeclass-structure.md) para la clase de C++ denominada como argumento. Los tres `CRuntimeClass` objetos pasados al constructor Document-template proporcionan la información necesaria para crear nuevos objetos de las clases especificadas durante el proceso de creación del documento. En el ejemplo se muestra la creación de una plantilla de documento que crea `CScribDoc` objetos con `CScribView` objetos adjuntos. Las vistas se enmarcan mediante ventanas de marco MDI secundarias estándar.

## <a name="see-also"></a>Consulte también

[Plantillas de documento y el proceso de creación de documentos y vistas](document-templates-and-the-document-view-creation-process.md)<br/>
[Crear documentos y vistas](document-view-creation.md)<br/>
[Relaciones entre objetos MFC](relationships-among-mfc-objects.md)<br/>
[Crear nuevos documentos, ventanas y vistas](creating-new-documents-windows-and-views.md)
