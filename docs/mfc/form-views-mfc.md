---
title: Vistas de formulario (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365297"
---
# <a name="form-views-mfc"></a>Vistas de formulario (MFC)

Puede agregar formularios a cualquier aplicación de Visual C++ que admita las bibliotecas MFC, `CFormView`incluida una aplicación basada en [formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) (una cuya clase de vista se deriva de ). Si no creó inicialmente la aplicación para admitir formularios, Visual C++ agregará esta compatibilidad automáticamente al insertar un nuevo formulario. En una aplicación SDI o MDI, que implementa la arquitectura de [documento/vista](../mfc/document-view-architecture.md)predeterminada, cuando el usuario elige el comando **Nuevo** (de forma predeterminada, en el menú **Archivo),** Visual C++ solicita al usuario que elija entre los formularios disponibles.

Con una aplicación SDI, cuando el usuario elige el comando **Nuevo,** la instancia actual del formulario continúa ejecutándose, pero se crea una nueva instancia de la aplicación con el formulario seleccionado si no se encuentra una. En una aplicación MDI, la instancia actual del formulario continúa ejecutándose cuando el usuario elige el comando **New.**

> [!NOTE]
> Puede insertar un formulario en una aplicación basada en cuadros de diálogo (una cuya clase de cuadro de diálogo se basa `CDialog` y otra en la que no se implementa ninguna clase de vista). Sin embargo, sin la arquitectura de documento/vista, Visual C++ no implementa automáticamente la funcionalidad **Archivo**&#124;**Nueva.** Debe crear una manera para que el usuario vea formularios adicionales, como implementar un cuadro de diálogo con fichas con varias páginas de propiedades.

Al insertar un nuevo formulario en la aplicación, Visual C++ hace lo siguiente:

- Crea una clase basada en una de las`CFormView`clases `CDaoRecordView`de `CDialog`estilo de formulario que elija ( , `CRecordView`, , o ).

- Crea un recurso de cuadro de diálogo con estilos adecuados (o puede usar un recurso de cuadro de diálogo existente que aún no se ha asociado a una clase).

   Si elige un recurso de cuadro de diálogo existente, es posible que deba establecer estos estilos mediante la página Propiedades del cuadro de diálogo. Los estilos de un cuadro de diálogo deben incluir:

     **WS_CHILD**en el

     **WS_BORDER**Off

     **WS_VISIBLE**off

     **WS_CAPTION**de salida

Para aplicaciones basadas en la arquitectura de documento/vista, el comando **Nuevo formulario** (haga clic con el botón derecho en la vista de clases) también:

- Crea `CDocument`una clase basada en

   En lugar de crear una nueva clase, puede usar cualquier clase `CDocument`basada existente en el proyecto.

- Genera una plantilla de `CDocument`documento (derivada de ) con recursos de cadena, menú e icono.

   También puede crear una nueva clase en la que basar la plantilla.

- Agrega una llamada `AddDocumentTemplate` al código `InitInstance` de la aplicación.

   Visual C++ agrega este código para cada nuevo formulario que cree, que agrega el formulario a la lista de formularios disponibles cuando el usuario elige el comando **Nuevo.** Este código incluye el identificador de recurso asociado del formulario y los nombres del documento asociado, la vista y las clases de marco que forman conjuntamente el nuevo objeto de formulario.

   Las plantillas de documento sirven como conexión entre documentos, ventanas de marco y vistas. Para un solo documento, puede crear muchas plantillas.

Para más información, consulte:

- [Crear una aplicación basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Inserción de un formulario en un proyecto](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
