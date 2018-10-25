---
title: Formulario de vistas (MFC) | Microsoft Docs
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
ms.openlocfilehash: 8236ed06a5863e2208c77294e4ddb7352b0f83f7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052998"
---
# <a name="form-views-mfc"></a>Vistas de formulario (MFC)

Puede agregar formularios a cualquier aplicación de Visual C++ que es compatible con las bibliotecas MFC, incluido un [aplicación basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md) (uno cuya clase de vista se deriva `CFormView`). Si no ha creado inicialmente la aplicación para admitir los formularios, Visual C++ agregará esta compatibilidad automáticamente cuando se inserta un nuevo formulario. En una aplicación SDI o MDI, que implementa el valor predeterminado [arquitectura documento/vista](../mfc/document-view-architecture.md), cuando el usuario elige el **New** comando (de forma predeterminada, en el **archivo** menú), Visual C++ pide al usuario elegir entre los formatos disponibles.

Con una aplicación SDI, cuando el usuario elige el **New** comando, la instancia actual del formulario sigue ejecutándose, pero se crea una nueva instancia de la aplicación con el formulario seleccionado si no se encontró ninguno. En una aplicación MDI, la instancia actual del formulario continúa ejecutándose cuando el usuario elige el **New** comando.

> [!NOTE]
>  Puede insertar un formulario en una aplicación basada en el cuadro de diálogo (uno cuya clase de cuadro de diálogo se basa en `CDialog` y otro en la vista que no se implementa la clase). Sin embargo, sin la arquitectura documento/vista, Visual C++ no implementa automáticamente la **archivo**&#124;**New** funcionalidad. Debe crear una forma para el usuario ver otras formas, como mediante la implementación de un cuadro de diálogo con pestañas con diversas páginas de propiedades.

Cuando se inserta un nuevo formulario en la aplicación, Visual C++ hace lo siguiente:

- Crea una clase basada en una de las clases de estilo de formato que elija (`CFormView`, `CRecordView`, `CDaoRecordView`, o `CDialog`).

- Crea un recurso de cuadro de diálogo con estilos apropiados (o puede usar un recurso de cuadro de diálogo existente que aún no se ha asociado con una clase).

   Si elige un recurso de cuadro de diálogo existente, deberá establecer estos estilos mediante la página de propiedades del cuadro de diálogo. Deben incluir los estilos para un cuadro de diálogo:

     **WS_CHILD**= On

     **WS_BORDER**= Off

     **WS_VISIBLE**= Off

     **WS_CAPTION =** desactivado

Para aplicaciones basadas en la arquitectura documento/vista, el **nuevo formulario** comando (clic derecho en la vista de clases) también:

- Crea un `CDocument`-clase basada en

   En lugar de tener que crear una clase nueva, puede usar cualquier existente `CDocument`-en función de clase del proyecto.

- Genera una plantilla de documento (derivado de `CDocument`) con recursos de cadena, menú e icono.

   También puede crear una nueva clase en el que se va a basar la plantilla.

- Agrega una llamada a `AddDocumentTemplate` en la aplicación `InitInstance` código.

   Visual C++ agrega este código para cada formulario nuevo creado, que agrega el formulario a la lista de formularios disponibles cuando el usuario elige el **New** comando. Este código incluye el identificador de recurso asociado del formulario y los nombres de las clases de marco que juntas componen el nuevo objeto de formulario, vista y documento asociado.

   Las plantillas de documento sirven como conexión entre documentos, ventanas de marco y vistas. Para un único documento, puede crear muchas de las plantillas.

Para obtener más información, consulte:

- [Crear una aplicación basada en formularios](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Inserción de un formulario en un proyecto](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
