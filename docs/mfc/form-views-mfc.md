---
title: Crear vistas (MFC) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a717ca80d84b884014a2567228829ffd87c5178
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930305"
---
# <a name="form-views-mfc"></a>Vistas de formulario (MFC)
Puede agregar formularios a cualquier aplicación de Visual C++ que admita las bibliotecas MFC, incluida una [aplicación basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) (uno cuya clase de vista se deriva de `CFormView`). Si no creó inicialmente la aplicación que admita formularios, Visual C++ agregará esta compatibilidad automáticamente al insertar un nuevo formulario. En una aplicación SDI o MDI, que implementa el valor predeterminado [arquitectura documento/vista](../mfc/document-view-architecture.md), cuando el usuario elige el **New** comando (de forma predeterminada, en la **archivo** menú), Visual C++ pide al usuario elegir entre los formatos disponibles.  
  
 Con una aplicación SDI, cuando el usuario elige el **New** comando, la instancia actual del formulario sigue ejecutándose, pero se crea una nueva instancia de la aplicación con el formulario seleccionado si no lo encuentra. En una aplicación MDI, la instancia actual del formulario sigue ejecutándose cuando el usuario elige el **New** comando.  
  
> [!NOTE]
>  Puede insertar un formulario en una aplicación basada en el cuadro de diálogo (uno cuya clase de cuadro de diálogo se basa en `CDialog` y otro en ninguna vista de qué clase se implementa). Sin embargo, sin la arquitectura documento/vista, Visual C++ no implementa automáticamente la **archivo**&#124;**New** funcionalidad. Debe crear una manera para que el usuario pueda ver formularios adicionales, como mediante la implementación de un cuadro de diálogo con fichas con diversas páginas de propiedades.  
  
 Cuando se inserta un nuevo formulario en la aplicación, Visual C++ hace lo siguiente:  
  
-   Crea una clase basada en una de las clases de estilo de formato que elija (`CFormView`, `CRecordView`, `CDaoRecordView`, o `CDialog`).  
  
-   Crea un recurso de cuadro de diálogo con estilos apropiados (o puede usar un recurso de cuadro de diálogo existente que aún no se ha asociado a una clase).  
  
     Si elige un recurso de cuadro de diálogo existente, debe establecer estos estilos mediante la página de propiedades para el cuadro de diálogo. Estilos para un cuadro de diálogo deben incluir:  
  
     **WS_CHILD**= On  
  
     **WS_BORDER**= Off  
  
     **WS_VISIBLE**= Off  
  
     **WS_CAPTION =** Off  
  
 Para aplicaciones basadas en la arquitectura documento/vista, la **nuevo formulario** comando (menú contextual en la vista de clases) también:  
  
-   Crea un `CDocument`-clase basada en  
  
     En lugar de tener que crear una clase nueva, puede usar cualquier existente `CDocument`-según la clase del proyecto.  
  
-   Genera una plantilla de documento (derivado de `CDocument`) con recursos de cadena, menú e icono.  
  
     También puede crear una nueva clase en la que se va a basar la plantilla.  
  
-   Agrega una llamada a `AddDocumentTemplate` en la aplicación `InitInstance` código.  
  
     Visual C++ agrega este código para cada formulario nuevo creado, lo cual agrega el formulario a la lista de formularios disponibles cuando el usuario elige el **New** comando. Este código incluye el identificador de recurso asociado del formulario y los nombres de las clases de marco que forman el nuevo objeto de formulario, vista y documento asociado.  
  
     Plantillas de documento sirven como conexión entre documentos, ventanas de marco y vistas. Para un único documento, puede crear muchas plantillas.  
  
 Para obtener más información, consulte:  
  
-   [Crear una aplicación basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Inserción de un formulario en un proyecto](../mfc/inserting-a-form-into-a-project.md)  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
