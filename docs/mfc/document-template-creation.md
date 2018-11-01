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
ms.openlocfilehash: f5c0691deab3d475a72cda0e86d681ea0c4ddfa0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480176"
---
# <a name="document-template-creation"></a>Clear plantillas de documentos

Al crear un nuevo documento en respuesta a un **New** o **abierto** comando desde el **archivo** menú, la plantilla de documento también crea una nueva ventana de marco a través de la que desea ver el documento.

El constructor de la plantilla de documento especifica qué tipos de documentos, ventanas y vistas que será capaz de crear la plantilla. Esto viene determinado por los argumentos pasados al constructor de la plantilla de documento. El código siguiente muestra la creación de un [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para una aplicación de ejemplo:

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

El puntero a un nuevo `CMultiDocTemplate` objeto se usa como argumento a [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumentos para el `CMultiDocTemplate` constructor incluir el identificador de recurso asociado con el tipo de documento menús y aceleradores, así como tres usos de la [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) macro. `RUNTIME_CLASS` Devuelve el [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objeto para la clase de C++ denominada como su argumento. Los tres `CRuntimeClass` objetos pasados al constructor de la plantilla de documento proporcionan la información necesaria para crear nuevos objetos de las clases especificadas durante el proceso de creación del documento. El ejemplo muestra la creación de una plantilla de documento que crea `CScribDoc` los objetos que tienen `CScribView` objetos adjuntos. Las vistas estándares ventanas de marco secundarias MDI enmarca.

## <a name="see-also"></a>Vea también

[Las plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Crear documentos y vistas](../mfc/document-view-creation.md)<br/>
[Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

