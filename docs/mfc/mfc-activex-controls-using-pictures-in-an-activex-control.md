---
title: 'Controles ActiveX MFC: Utilizar imágenes en un control ActiveX'
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 1f78823f39417ff6928a1b915d83507bc1ac9526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358290"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>Controles ActiveX MFC: Utilizar imágenes en un control ActiveX

En este artículo se describe el tipo de imagen común y cómo implementarlo en el control ActiveX. Contenido de los temas:

- [Descripción general de las propiedades de imagen personalizadas](#_core_overview_of_custom_picture_properties)

- [Implementar una propiedad de imagen personalizada en el control ActiveX](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [Adiciones a su proyecto de control](#_core_additions_to_your_control_project)

## <a name="overview-of-custom-picture-properties"></a><a name="_core_overview_of_custom_picture_properties"></a> Información general sobre las propiedades de imagen personalizadas

Un tipo de imagen es una opción de un grupo de tipos comunes para algunos controles ActiveX. El tipo de imagen controla los metarchivos, los mapas de bits o los iconos y permite al usuario especificar una imagen que se mostrará en un control ActiveX. Las propiedades de imagen personalizadas se implementan mediante un objeto de imagen y las funciones Get/Set que permiten controlar el acceso de usuario a la propiedad de imagen. Control el acceso de usuarios a la propiedad de imagen personalizada mediante la página de propiedades de imágenes estándar.

Además del tipo de imagen estándar, también están disponibles los tipos de fuente y color. Para obtener más información sobre el uso del tipo de fuente estándar en el control ActiveX, vea el artículo [Controles ActiveX MFC: Usar fuentes](../mfc/mfc-activex-controls-using-fonts.md).

Las clases de controles ActiveX proporcionan varios componentes que puede usar para implementar la propiedad de imagen en el control. Estos componentes incluyen:

- La clase [CPictureHolder](../mfc/reference/cpictureholder-class.md) .

   Esta clase proporciona fácil acceso a la funcionalidad y al objeto de imagen del elemento mostrado por la propiedad de imagen personalizada.

- Compatibilidad con las propiedades de tipo **LPPICTUREDISP**, implementadas con las funciones Get/Set.

   Con la vista de clases, puede agregar rápidamente una propiedad personalizada (o varias) que admita el tipo de imagen. Para obtener más información sobre la adición de propiedades de controles ActiveX con la vista de clases, vea el [Controles ActiveX MFC: Propiedades](../mfc/mfc-activex-controls-properties.md).

- Página de propiedades que manipula la propiedad o las propiedades de imagen de un control.

   Esta página de propiedades forma parte de un grupo de páginas de propiedades estándar disponibles para los controles ActiveX. Para obtener más información sobre las páginas de propiedades de controles ActiveX, vea el [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md).

## <a name="implementing-a-custom-picture-property-in-your-activex-control"></a><a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a>Implementación de una propiedad de imagen personalizada en el control ActiveX

Cuando complete los pasos que se describen en esta sección, el control podrá mostrar imágenes elegidas por el usuario. El usuario puede cambiar la imagen mostrada mediante una página de propiedades que muestra la imagen actual y tiene un botón Examinar que permite que el usuario seleccione diferentes imágenes.

Una propiedad de imagen personalizada se implementa mediante un proceso similar al usado para implementar otras propiedades; la diferencia principal radica en que la propiedad personalizada debe admitir un tipo de imagen. Dado que el elemento de la propiedad de imagen se debe dibujar con el control ActiveX, deben realizarse varias adiciones y modificaciones en la propiedad para que pueda implementarse totalmente.

Para implementar una propiedad de imagen personalizada, debe hacer lo siguiente:

- [Agregar código al proyecto de control](#_core_additions_to_your_control_project).

   Se deben agregar un identificador de página de propiedades de imagen estándar, un miembro de datos de tipo `CPictureHolder`y una propiedad personalizada de tipo **LPPICTUREDISP** con una implementación Get/Set.

- [Modificar varias funciones en la clase del control](#_core_modifications_to_your_control_project).

   Estas modificaciones se realizarán en varias funciones que son responsables del dibujo del control ActiveX.

## <a name="additions-to-your-control-project"></a><a name="_core_additions_to_your_control_project"></a> Adiciones al proyecto de control

Para agregar el identificador de página de propiedades para la página de propiedades Picture estándar, inserte la línea siguiente después de la macro BEGIN_PROPPAGEIDS en el archivo de implementación del control (. CPP):

[!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

También debe incrementar el parámetro count de la macro de BEGIN_PROPPAGEIDS en uno. Esto se ilustra en la línea siguiente:

[!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

Para agregar el miembro de datos `CPictureHolder` a la clase de control, inserte la siguiente línea en la sección protegida de la declaración de clase del control en el archivo de encabezado del control (. (H):

[!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

No es necesario asignar un nombre al miembro de datos *m_pic;* cualquier nombre será suficiente.

A continuación, agregue una propiedad personalizada que admita un tipo de imagen:

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>Para agregar una propiedad de imagen personalizada mediante el Asistente para agregar propiedades

1. Cargue el proyecto del control.

1. En la vista de clases, expanda el nodo de biblioteca del control.

1. Haga clic con el botón derecho en el nodo de interfaz del control (el segundo nodo del nodo de biblioteca) para abrir el menú contextual.

1. En el menú contextual, elija **Agregar** y, luego, **Agregar propiedad**.

1. En el cuadro **Nombre de propiedad** , escriba el nombre de la propiedad. Con fines de ejemplo, `ControlPicture` se utiliza en este procedimiento.

1. En el cuadro Tipo de **propiedad,** seleccione **IPictureDisp** <strong>\*</strong> para el tipo de propiedad.

1. Para **Tipo de implementación**, haga clic en **Métodos Get/Set**.

1. Escriba nombres únicos para las funciones Get y Set o acepte los nombres predeterminados. (En este ejemplo, se usan los nombres predeterminados `GetControlPicture` y `SetControlPicture` ).

1. Haga clic en **Finalizar**

El Asistente para agregar propiedades agrega el siguiente código entre los comentarios del mapa de envíos en el archivo de encabezado del control (.H):

[!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

Además, se insertó el siguiente código en el mapa de envíos del archivo de implementación del control (.CPP):

[!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

El Asistente para agregar propiedades también agrega las dos siguientes funciones de código auxiliar en el archivo de implementación:

[!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
> Los nombres de clase y función del control pueden diferir de los del ejemplo anterior.

### <a name="modifications-to-your-control-project"></a><a name="_core_modifications_to_your_control_project"></a>Modificaciones a su proyecto de control

Después de realizar las adiciones necesarias en el proyecto de control, debe modificar varias funciones que afectan a la representación del control ActiveX. Estas funciones, `OnResetState`, `OnDraw`y las funciones Get/Set de una propiedad de imagen personalizada se encuentran en el archivo de implementación. (Tenga en cuenta que en `CSampleCtrl`este `CPictureHolder` ejemplo se llama a la clase de `ControlPicture`control , se llama al miembro de datos *m_pic*y el nombre de propiedad de imagen personalizado es .)

En la función `OnResetState` del control, agregue la siguiente línea opcional después de la llamada a `COleControl::OnResetState`:

[!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

De este modo, la imagen del control se establece en una imagen en blanco.

Para dibujar la imagen correctamente, realice una llamada a [CPictureHolder::Render](../mfc/reference/cpictureholder-class.md#render) en la función `OnDraw` del control. Modifique la función para que sea similar a la del ejemplo siguiente:

[!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

En la función Get de la propiedad de imagen personalizada del control, agregue la siguiente línea:

[!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

En la función Set de la propiedad de imagen personalizada del control, agregue las líneas siguientes:

[!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

La propiedad de imagen debe hacerse persistente para que la información que se agregue durante el diseño se muestre en tiempo de ejecución. Agregue la siguiente línea a la función `COleControl`de la clase derivada de `DoPropExchange` :

[!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
> Los nombres de clase y función pueden diferir de los del ejemplo anterior.

Después de completar las modificaciones, vuelva a generar el proyecto para incorporar la nueva funcionalidad de la propiedad de imagen personalizada y use el contenedor de prueba para probar la nueva propiedad. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Usar fuentes](../mfc/mfc-activex-controls-using-fonts.md)<br/>
[Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)
