---
title: Crear una aplicación MFC basada en formularios
ms.date: 09/09/2019
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 1dbbc5c29f85ced846cb3e07a02a5d6a55c94b20
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908051"
---
# <a name="creating-a-forms-based-mfc-application"></a>Crear una aplicación MFC basada en formularios

Un formulario es un cuadro de diálogo con controles que permiten a un usuario tener acceso a datos y, posiblemente, modificarlos. Es posible que quiera desarrollar una aplicación en la que el usuario elija entre un conjunto de formularios. Normalmente, una aplicación basada en formularios permite al usuario obtener acceso a los formularios haciendo clic en **nuevo** en el menú **archivo** . Una aplicación basada en cuadros de diálogo, que no proporciona a los usuarios acceso a una **nueva** opción en el menú **archivo** , también se considera una aplicación basada en formularios.

Una aplicación basada en formularios de interfaz de un único documento (SDI) sólo permite que se ejecute una instancia de un formulario concreto cada vez. Es posible ejecutar diferentes formas a la vez desde una aplicación basada en formularios SDI seleccionando un nuevo formulario en la opción **nuevo** del menú **archivo** .

Si crea una aplicación basada en formularios de interfaz de múltiples documentos (MDI), la aplicación permitirá el uso de varias instancias del mismo formulario.

Si crea una aplicación que admita varios documentos de nivel superior, el escritorio será la ventana primaria implícita del documento y el marco del documento no se restringirá al área de cliente de la aplicación. Puede abrir varias instancias del documento, cada una con su marco, su menú y su icono de la barra de tareas. Puede cerrar individualmente las instancias posteriores de documentos, pero si selecciona la opción **salir** en el menú **archivo** de la instancia inicial, la aplicación cierra todas las instancias.

Las aplicaciones SDI, MDI y de múltiples documentos de nivel superior son todas aplicaciones basadas en formularios y utilizan la arquitectura documento/vista.

Cualquier aplicación basada en un cuadro de diálogo es, por definición, una aplicación basada en formularios. Una aplicación basada en un cuadro de diálogo no utiliza la arquitectura documento/vista, por lo que el programador deberá administrar los métodos de creación y acceso para sus propios formularios adicionales.

La clase base para las aplicaciones basadas en formularios es [CFormView](cformview-class.md). Si la aplicación ofrece compatibilidad con bases de datos, también puede seleccionar cualquier clase que se derive de `CFormView`. Un formulario es cualquier ventana derivada de `CFormView` o de cualquier clase que herede de `CFormView`.

Incluso si usa una clase base como [CView](cview-class.md), puede hacer que las aplicaciones se basen en formularios mediante la [adición de una clase MFC](adding-an-mfc-class.md) derivada `CFormView`de.

Cuando finalice el asistente, se abrirá el proyecto y, si seleccionó `CFormView` (o una clase que herede de `CFormView`) como clase base o creó una aplicación basada en un cuadro de diálogo, Visual C++ abrirá el editor de cuadros de diálogo. En este momento ya está preparado para diseñar su primer formulario.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Para empezar a crear un ejecutable MFC basado en formularios

1. Siga las instrucciones de [creación de una aplicación MFC](creating-an-mfc-application.md) para una aplicación MFC basada en formularios.

1. En la página tipo de [aplicación](application-type-mfc-application-wizard.md) del Asistente para aplicaciones MFC, active la casilla **compatibilidad con la arquitectura de documento/vista** .

1. Seleccione **un único documento**, **varios documentos**o **varios documentos de nivel superior**.

    > [!NOTE]
    >  Si eligió una aplicación de interfaz de documentos de nivel superior SDI, MDI o varias, `CView` se establece de forma predeterminada como la clase base de la vista de la aplicación en la página [clases generadas](generated-classes-mfc-application-wizard.md) del asistente. Para crear una aplicación basada en formularios, debe seleccionar `CFormView` como clase base de la vista de la aplicación. Tenga en cuenta que el asistente no proporciona compatibilidad con la impresión para una aplicación basada en formularios.

1. Establezca las demás opciones de proyecto que desee en las otras páginas del asistente.

1. Haga clic en **Finalizar** para generar la aplicación esqueleto.

Para más información, consulte:

- [Clases de vistas derivadas](../derived-view-classes-available-in-mfc.md)

- [Alternativas a la arquitectura documento/vista](../alternatives-to-the-document-view-architecture.md)

- [Opciones de diseño de aplicaciones](../application-design-choices.md)

## <a name="see-also"></a>Vea también

[Asistente para aplicaciones MFC](mfc-application-wizard.md)<br/>
[Vistas de formulario](../form-views-mfc.md)<br/>
[Creación de una aplicación MFC estilo Explorador de archivos](creating-a-file-explorer-style-mfc-application.md)<br/>
[Creación de una aplicación MFC estilo explorador web](creating-a-web-browser-style-mfc-application.md)
