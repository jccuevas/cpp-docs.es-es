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
ms.openlocfilehash: 94d8b7d026ee3aaf1bac9dee2226de6dd9382599
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615680"
---
# <a name="form-views-mfc"></a>Vistas de formulario (MFC)

Puede Agregar formularios a cualquier aplicación Visual C++ que admita las bibliotecas MFC, incluida una [aplicación basada en formularios](reference/creating-a-forms-based-mfc-application.md) (una cuya clase de vista se deriva de `CFormView` ). Si no ha creado inicialmente la aplicación para admitir formularios, Visual C++ agregará esta compatibilidad cuando inserte un nuevo formulario. En una aplicación SDI o MDI, que implementa la arquitectura de [documento/vista](document-view-architecture.md)predeterminada, cuando el usuario elige el comando **nuevo** (de forma predeterminada, en el menú **archivo** ), Visual C++ solicita al usuario que elija entre los formularios disponibles.

Con una aplicación SDI, cuando el usuario elige el comando **nuevo** , la instancia actual del formulario continúa ejecutándose, pero se crea una nueva instancia de la aplicación con el formulario seleccionado si no se encuentra ninguna. En una aplicación MDI, la instancia actual del formulario continúa ejecutándose cuando el usuario elige el **nuevo** comando.

> [!NOTE]
> Puede insertar un formulario en una aplicación basada en cuadros de diálogo (una cuya clase de cuadro de diálogo se basa en `CDialog` y otra en la que no se implementa ninguna clase de vista). Sin embargo, sin la arquitectura de documento/vista, Visual C++ no implementa automáticamente el **archivo**&#124;**nueva** funcionalidad. Debe crear una manera para que el usuario vea formularios adicionales, como implementar un cuadro de diálogo con pestañas con varias páginas de propiedades.

Al insertar un nuevo formulario en la aplicación, Visual C++ hace lo siguiente:

- Crea una clase basada en una de las clases de estilo de formulario que elija ( `CFormView` , `CRecordView` , `CDaoRecordView` o `CDialog` ).

- Crea un recurso de cuadro de diálogo con los estilos adecuados (o puede usar un recurso de diálogo existente que todavía no se ha asociado a una clase).

   Si elige un recurso de diálogo existente, puede que tenga que establecer estos estilos mediante la página Propiedades del cuadro de diálogo. Los estilos de un cuadro de diálogo deben incluir:

     **WS_CHILD**= on

     **WS_BORDER**= OFF

     **WS_VISIBLE**= OFF

     **WS_CAPTION**= OFF

En el caso de las aplicaciones basadas en la arquitectura documento/vista, el comando **nuevo formulario** (haga clic con el botón derecho en vista de clases) también:

- Crea una `CDocument` clase basada en.

   En lugar de crear una nueva clase, puede usar cualquier `CDocument` clase basada en existente en el proyecto.

- Genera una plantilla de documento (derivada de `CDocument` ) con recursos de cadena, menú e icono.

   También puede crear una nueva clase en la que basar la plantilla.

- Agrega una llamada a `AddDocumentTemplate` en el código de la aplicación `InitInstance` .

   Visual C++ agrega este código para cada nuevo formulario que cree, que agrega el formulario a la lista de formularios disponibles cuando el usuario elige el **nuevo** comando. Este código incluye el identificador de recurso asociado del formulario y los nombres de las clases de documento, vista y marco asociados que forman conjuntamente el nuevo objeto de formulario.

   Las plantillas de documento sirven como conexión entre documentos, ventanas de marco y vistas. Para un único documento, puede crear muchas plantillas.

Para obtener más información, consulte:

- [Crear una aplicación basada en formularios](reference/creating-a-forms-based-mfc-application.md)

- [Inserción de un formulario en un proyecto](inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)
