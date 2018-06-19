---
title: Creación de una plantilla de documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36650e0ae1ce042a887c6a87d1bbe62d8b6d7fe4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345799"
---
# <a name="document-template-creation"></a>Clear plantillas de documentos
Al crear un nuevo documento en respuesta a un `New` o **abiertos** línea de comandos desde el **archivo** menú, la plantilla de documento también crea una nueva ventana de marco a través de la que se va a ver el documento.  
  
 El constructor de la plantilla de documento especifica qué tipos de documentos, ventanas y vistas que podrá crear la plantilla. Esto viene determinado por los argumentos que se pasan al constructor de la plantilla de documento. El código siguiente muestra la creación de un [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para una aplicación de ejemplo:  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]  
  
 El puntero a una nueva `CMultiDocTemplate` objeto se usa como argumento para [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate). Argumentos para el `CMultiDocTemplate` constructor incluir el identificador de recurso asociado con el tipo de documento menús y aceleradores, así como tres usos de la [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) macro. `RUNTIME_CLASS` Devuelve el [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objeto para la clase de C++ denominada como su argumento. Los tres `CRuntimeClass` objetos pasados al constructor de la plantilla de documento proporcionan la información necesaria para crear nuevos objetos de las clases especificadas durante el proceso de creación de documento. En el ejemplo se muestra la creación de una plantilla de documento que crea `CScribDoc` objetos que tienen `CScribView` objetos asociados. Las vistas son enmarcadas por ventanas de marco secundarias MDI estándares.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de documento y el proceso de creación de documento/vista](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Creación de documento/vista](../mfc/document-view-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)   
 [Creación de nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)

