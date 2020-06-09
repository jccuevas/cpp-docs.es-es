---
title: 'Controles ActiveX MFC: Páginas de propiedades'
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: 3d22085daa503a7c778111718445920f98b98a89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615436"
---
# <a name="mfc-activex-controls-property-pages"></a>Controles ActiveX MFC: Páginas de propiedades

Las páginas de propiedades permiten a un usuario del control ActiveX ver y cambiar las propiedades de los controles ActiveX. Se tiene acceso a estas propiedades mediante la invocación de un cuadro de diálogo de propiedades de control que contiene una o varias páginas de propiedades que proporcionan una interfaz gráfica personalizada para ver y editar las propiedades del control.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Las páginas de propiedades de controles ActiveX se muestran de dos maneras:

- Cuando se invoca el verbo de las propiedades del control (**OLEIVERB_PROPERTIES**), el control abre un cuadro de diálogo de propiedades modal que contiene las páginas de propiedades del control.

- El contenedor puede mostrar su propio cuadro de diálogo no modal que muestra las páginas de propiedades del control seleccionado.

El cuadro de diálogo Propiedades (que se muestra en la ilustración siguiente) se compone de un área para mostrar la página de propiedades actual, pestañas para cambiar entre las páginas de propiedades y una colección de botones que realizan tareas comunes, como cerrar el cuadro de diálogo de la página de propiedades, cancelar los cambios realizados o aplicar inmediatamente cualquier cambio en el control ActiveX.

![Cuadro de diálogo de propiedades de Circ3](../mfc/media/vc373i1.gif "Cuadro de diálogo de propiedades de Circ3") <br/>
Cuadro de diálogo Propiedades

En este artículo se tratan temas relacionados con el uso de páginas de propiedades en un control ActiveX. Se incluyen los siguientes:

- [Implementar la página de propiedades predeterminada de un control ActiveX](#_core_implementing_the_default_property_page)

- [Agregar controles a una página de propiedades](#_core_adding_controls_to_a_property_page)

- [Personalización de la función DoDataExchange](#_core_customizing_the_dodataexchange_function)

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:

- [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](mfc-activex-controls-adding-another-custom-property-page.md)

- [Controles ActiveX MFC: Usar páginas de propiedades estándar](mfc-activex-controls-using-stock-property-pages.md)

Para obtener información sobre el uso de hojas de propiedades en una aplicación MFC que no sea un control ActiveX, vea [hojas de propiedades](property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementación de la página de propiedades predeterminada

Si utiliza el Asistente para controles ActiveX para crear el proyecto de control, el Asistente para controles ActiveX proporciona una clase de página de propiedades predeterminada para el control derivado de la [clase COlePropertyPage](reference/colepropertypage-class.md). Inicialmente, esta página de propiedades está en blanco, pero puede agregarle cualquier control de cuadro de diálogo o conjunto de controles. Dado que el Asistente para controles ActiveX solo crea una clase de página de propiedades de forma predeterminada, las clases de página de propiedades adicionales (también derivadas de `COlePropertyPage` ) se deben crear utilizando vista de clases. Para obtener más información sobre este procedimiento, vea [controles ActiveX MFC: agregar otra página de propiedades personalizada](mfc-activex-controls-adding-another-custom-property-page.md).

La implementación de una página de propiedades (en este caso, el valor predeterminado) es un proceso de tres pasos:

#### <a name="to-implement-a-property-page"></a>Para implementar una página de propiedades

1. Agregue una `COlePropertyPage` clase derivada de al proyecto de control. Si el proyecto se creó mediante el Asistente para controles ActiveX (como en este caso), la clase de página de propiedades predeterminada ya existe.

1. Utilice el editor de cuadros de diálogo para agregar controles a la plantilla de la página de propiedades.

1. Personalice la `DoDataExchange` función de la `COlePropertyPage` clase derivada de para intercambiar valores entre el control de página de propiedades y el control ActiveX.

Por ejemplo, en los procedimientos siguientes se usa un control simple (denominado "sample"). El ejemplo se ha creado mediante el Asistente para controles ActiveX y solo contiene la propiedad Caption estándar.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Agregar controles a una página de propiedades

#### <a name="to-add-controls-to-a-property-page"></a>Para agregar controles a una página de propiedades

1. Con el proyecto de control abierto, abra Vista de recursos.

1. Haga doble clic en el icono directorio del **cuadro de diálogo** .

1. Abra el cuadro de diálogo IDD_PROPPAGE_SAMPLE.

   El Asistente para controles ActiveX anexa el nombre del proyecto al final del identificador del cuadro de diálogo, en este caso, sample.

1. Arrastre y coloque el control seleccionado desde el cuadro de herramientas en el área del cuadro de diálogo.

1. En este ejemplo, el control de etiqueta de texto "Caption:" y un control de cuadro de edición con un identificador IDC_CAPTION son suficientes.

1. Haga clic en **Guardar** en la barra de herramientas para guardar los cambios.

Ahora que se ha modificado la interfaz de usuario, debe vincular el cuadro de edición con la propiedad Caption. Esto se hace en la siguiente sección editando la `CSamplePropPage::DoDataExchange` función.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Personalización de la función DoDataExchange

La función oDataExchange de la página de propiedades [CWnd::D](reference/cwnd-class.md#dodataexchange) permite vincular los valores de las páginas de propiedades con los valores reales de las propiedades del control. Para establecer vínculos, debe asignar los campos de página de propiedades adecuados a sus propiedades de control respectivas.

Estas asignaciones se implementan mediante la página de propiedades **DDP_** funciones. Las funciones de **DDP_** funcionan como las funciones de **DDX_** que se usan en los cuadros de diálogo estándar de MFC, con una excepción. Además de la referencia a una variable miembro, **DDP_** funciones toman el nombre de la propiedad de control. A continuación se encuentra una entrada típica en la `DoDataExchange` función de una página de propiedades.

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Esta función asocia la variable miembro de *m_caption* de la página de propiedades con el título, mediante la `DDP_TEXT` función.

Una vez insertado el control de la página de propiedades, debe establecer un vínculo entre el control de la página de propiedades, IDC_CAPTION, y la propiedad de control real, Caption, usando la `DDP_Text` función tal y como se ha descrito anteriormente.

[Las páginas de propiedades](reference/property-pages-mfc.md) están disponibles para otros tipos de controles de cuadro de diálogo, como las casillas, los botones de radio y los cuadros de lista. En la tabla siguiente se muestra el conjunto completo de funciones de **DDP_** de página de propiedades y sus propósitos:

### <a name="property-page-functions"></a>Funciones de la página de propiedades

|Nombre de función|Usar esta función para vincular|
|-------------------|-------------------------------|
|`DDP_CBIndex`|Índice de la cadena seleccionada en un cuadro combinado con una propiedad de control.|
|`DDP_CBString`|Cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras que el valor de la propiedad, pero no es necesario que coincida completamente.|
|`DDP_CBStringExact`|Cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|`DDP_Check`|Una casilla con una propiedad de control.|
|`DDP_LBIndex`|Índice de la cadena seleccionada en un cuadro de lista con una propiedad de control.|
|`DDP_LBString`|Cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras que el valor de la propiedad, pero no es necesario que coincida completamente.|
|`DDP_LBStringExact`|Cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|`DDP_Radio`|Botón de radio con una propiedad de control.|
|`DDP_Text`|Texto con una propiedad de control.|

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[COlePropertyPage (clase)](reference/colepropertypage-class.md)
