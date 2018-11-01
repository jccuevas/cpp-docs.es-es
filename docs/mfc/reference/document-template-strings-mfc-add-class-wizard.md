---
title: Cadenas de plantillas de documentos, Asistente para agregar clases MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
ms.openlocfilehash: a5664a539af351051f9ae3642c089e51b54bc8cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662428"
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Cadenas de plantillas de documentos, Asistente para agregar clases MFC

Esta página del asistente solo está disponible para las clases que cumplen los criterios siguientes:

- El proyecto MFC es compatible con la arquitectura documento/vista.

- Es la clase base de la nueva clase [CFormView](../../mfc/reference/cformview-class.md).

- La casilla de verificación **generar recursos DocTemplate** se comprueba en el **nombres** sección de la [Asistente para clases MFC](../../mfc/reference/mfc-add-class-wizard.md).

El asistente proporciona valores predeterminados para los valores siguientes ayudar con la vista Diseño de formularios, administración y localización. Dado que la mayoría de las cadenas de plantilla de documento son visibles y las utilizan los usuarios del formulario, se traducen el **idioma de recurso** indicado en el [tipos de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página del Asistente para aplicaciones MFC Cuando se creó el proyecto.

> [!NOTE]
>  El asistente no proporciona automáticamente compatibilidad con impresión para las clases derivadas de `CFormView`.

Consulte [plantillas de documento y el proceso de creación de documento/vista](../../mfc/document-templates-and-the-document-view-creation-process.md) para obtener más información.

## <a name="nonlocalized-strings"></a>Cadenas no localizadas

Se aplica a las aplicaciones que crean documentos de usuario. Los usuarios pueden abrir y guardar los documentos más fácilmente si el tipo de documento tiene una extensión de archivo y un identificador de tipo de archivo. Estos elementos no están localizados, ya que se usan por el sistema en lugar de por el usuario.

- **Extensión de archivo**

   Establece la extensión de archivo asociada con el tipo de documento para esta aplicación de formularios. La extensión predeterminada se basa en el nombre de clase. Por ejemplo, si la nueva clase MFC se denomina `CWidget`, de forma predeterminada, la extensión de archivo es. wid. La extensión de archivo se utiliza en filtros de archivo y la **abierto** y **Guardar como** cuadros de diálogo.

   Si cambia la extensión de archivo, el cambio se refleja en el **nombre filtro** cuadro.

   > [!NOTE]
   > Si cambia la extensión de archivo de forma predeterminada, no incluya el período.

- **Id. de tipo de archivo**

   Establece la etiqueta para el tipo de documento en el registro del sistema.

## <a name="localized-strings"></a>Cadenas localizadas

Genera cadenas asociadas a los formularios y documentos que se leen y se utilizan los usuarios de la aplicación, por lo que las cadenas están localizadas.

- **Nombre del tipo de documento**

   Identifica el tipo de documento en la que se puede agrupar un documento de la aplicación. De forma predeterminada, se basa en el nombre de la clase. Por ejemplo, si la nueva clase MFC se denomina **CWidget**, de forma predeterminada, el nombre de tipo de documento es Widget. Cambiar el valor predeterminado, no cambie ninguna otra opción en este cuadro de diálogo.

- **Nombre de filtro**

   Establece el nombre que los usuarios pueden indicar para buscar archivos de tipo de archivo especificado. Esta opción está disponible desde el **archivos de tipo** y **Guardar como tipo** opciones en el estándar Windows **abierto** y **Guardar como** cuadros de diálogo. De forma predeterminada, el nombre se basa en el nombre del proyecto más archivos, seguidos por la extensión indican en **extensión de archivo**. Por ejemplo, si el proyecto se denomina Widget y la extensión de archivo es .wid, el **nombre filtro** será archivos Widget (*.wid) de forma predeterminada.

- **Nuevo nombre corto del archivo**

   Establece el nombre que aparece en el Windows estándar **New** cuadro de diálogo, si el proyecto tiene más de una plantilla de documento. Si la aplicación es un [servidor de automatización](../../mfc/automation-servers.md), este nombre se usa como el nombre corto del objeto de automatización. De forma predeterminada, este nombre se basa en el nombre de clase.

- **Nombre largo del tipo de archivo**

   Establece el nombre de tipo de archivo en el registro del sistema. Si la aplicación es un servidor de Automation, este nombre se usa como el nombre largo de su objeto de automatización. De forma predeterminada, este nombre se basa en el nombre de clase más. Documento. Por ejemplo, si es el nombre de clase `CWidget`, **tipo de archivo, nombre largo** es documento Widget.

- **Clase de documento**

   Indica la clase de documento del proyecto. De forma predeterminada, esta clase es una clase de documento de la aplicación principal, como se muestra en el [revisar las clases generadas](../../mfc/reference/generated-classes-mfc-application-wizard.md) página del Asistente para aplicaciones MFC. Puede seleccionar otra clase de documento en la lista, si se han agregado otras clases de documento en el proyecto.

## <a name="see-also"></a>Vea también

[Asistente para agregar clases MFC](../../mfc/reference/mfc-add-class-wizard.md)<br/>
[Clase MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)
