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
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364566"
---
# <a name="mfc-activex-controls-property-pages"></a>Controles ActiveX MFC: Páginas de propiedades

Las páginas de propiedades permiten a un usuario de control ActiveX ver y cambiar las propiedades del control ActiveX. Se tiene acceso a estas propiedades invocando un cuadro de diálogo de propiedades de control, que contiene una o varias páginas de propiedades que proporcionan una interfaz gráfica personalizada para ver y editar las propiedades del control.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Las páginas de propiedades del control ActiveX se muestran de dos maneras:

- Cuando se invoca el verbo Properties del control (**OLEIVERB_PROPERTIES**), el control abre un cuadro de diálogo de propiedad modal que contiene las páginas de propiedades del control.

- El contenedor puede mostrar su propio cuadro de diálogo no quese mostró las páginas de propiedades del control seleccionado.

El cuadro de diálogo de propiedades (ilustrado en la figura siguiente) consta de un área para mostrar la página de propiedades actual, fichas para cambiar entre páginas de propiedades y una colección de botones que realizan tareas comunes como cerrar el cuadro de diálogo de página de propiedades, cancelar los cambios realizados o aplicar inmediatamente los cambios al control ActiveX.

![Cuadro de diálogo de propiedades de Circ3](../mfc/media/vc373i1.gif "Cuadro de diálogo de propiedades de Circ3") <br/>
Cuadro de diálogo Propiedades

En este artículo se tratan temas relacionados con el uso de páginas de propiedades en un control ActiveX. Entre ellas se incluyen las siguientes:

- [Implementación de la página de propiedades predeterminada para un control ActiveX](#_core_implementing_the_default_property_page)

- [Agregar controles a una página de propiedades](#_core_adding_controls_to_a_property_page)

- [Personalización de la función DoDataExchange](#_core_customizing_the_dodataexchange_function)

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, consulte los artículos siguientes:

- [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)

Para obtener información sobre el uso de hojas de propiedades en una aplicación MFC que no sea un control ActiveX, vea [Hojas de propiedades](../mfc/property-sheets-mfc.md).

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>Implementación de la página de propiedades predeterminada

Si utiliza el Asistente para controles ActiveX para crear el proyecto de control, el Asistente para controles ActiveX proporciona una clase de página de propiedades predeterminada para el control derivado de [COlePropertyPage (Clase).](../mfc/reference/colepropertypage-class.md) Inicialmente, esta página de propiedades está en blanco, pero puede agregarle cualquier control de cuadro de diálogo o conjunto de controles. Dado que el Asistente para controles ActiveX crea solo una clase de `COlePropertyPage`página de propiedades de forma predeterminada, se deben crear clases de página de propiedades adicionales (también derivadas de ) mediante la vista de clases. Para obtener más información sobre este procedimiento, vea [Controles ActiveX de MFC: agregar otra página](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)de propiedades personalizadas .

Implementar una página de propiedades (en este caso, el valor predeterminado) es un proceso de tres pasos:

#### <a name="to-implement-a-property-page"></a>Para implementar una página de propiedades

1. Agregue `COlePropertyPage`una clase derivada al proyecto de control. Si el proyecto se creó mediante el Asistente para controles ActiveX (como en este caso), la clase de página de propiedades predeterminada ya existe.

1. Utilice el editor de cuadros de diálogo para agregar controles a la plantilla de página de propiedades.

1. Personalice `DoDataExchange` la `COlePropertyPage`función de la -derived clase para intercambiar valores entre el control de página de propiedades y el control ActiveX.

Por ejemplo, los procedimientos siguientes usan un control simple (denominado "Sample"). El ejemplo se creó mediante el Asistente para controles ActiveX y contiene solo la propiedad stock Caption.

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>Agregar controles a una página de propiedades

#### <a name="to-add-controls-to-a-property-page"></a>Para agregar controles a una página de propiedades

1. Con el proyecto de control abierto, abra la vista de recursos.

1. Haga doble clic en el icono del directorio **Diálogo.**

1. Abra el cuadro de diálogo IDD_PROPPAGE_SAMPLE.

   El Asistente para controles ActiveX anexa el nombre del proyecto al final del identificador de cuadro de diálogo, en este caso, Ejemplo.

1. Arrastre y suelte el control seleccionado desde el cuadro de herramientas hasta el área del cuadro de diálogo.

1. En este ejemplo, un control de etiqueta de texto "Caption :" y un control de cuadro de edición con un identificador de IDC_CAPTION son suficientes.

1. Haga clic en **Guardar** en la barra de herramientas para guardar los cambios.

Ahora que se ha modificado la interfaz de usuario, debe vincular el cuadro de edición con el Caption propiedad. Esto se hace en la `CSamplePropPage::DoDataExchange` siguiente sección editando la función.

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>Personalización de la función DoDataExchange

La página de propiedades [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) función le permite vincular valores de página de propiedades con los valores reales de propiedades en el control. Para establecer vínculos, debe asignar los campos de página de propiedades adecuados a sus respectivas propiedades de control.

Estas asignaciones se implementan mediante la página de propiedades **DDP_** funciones. Las **funciones DDP_** funcionan como las funciones **DDX_** utilizadas en los cuadros de diálogo estándar de MFC, con una excepción. Además de la referencia a una variable miembro, **DDP_** funciones toman el nombre de la propiedad de control. A continuación se muestra `DoDataExchange` una entrada típica en la función de una página de propiedades.

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

Esta función asocia la variable miembro *m_caption* de `DDP_TEXT` la página de propiedades con el título, mediante la función.

Después de insertar el control de página de propiedades, debe establecer un vínculo entre el control `DDP_Text` de página de propiedades, IDC_CAPTION y la propiedad de control real, Caption, utilizando la función como se ha descrito anteriormente.

[Las páginas](../mfc/reference/property-pages-mfc.md) de propiedades están disponibles para otros tipos de control de cuadro de diálogo, como casillas de verificación, botones de opción y cuadros de lista. La tabla siguiente enumera todo el conjunto de funciones **de DDP_** página de propiedades y sus propósitos:

### <a name="property-page-functions"></a>Funciones de página de propiedades

|Nombre de función|Utilice esta función para vincular|
|-------------------|-------------------------------|
|`DDP_CBIndex`|El índice de la cadena seleccionada en un cuadro combinado con una propiedad de control.|
|`DDP_CBString`|La cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras que el valor de la propiedad, pero no es necesario que coincida completamente.|
|`DDP_CBStringExact`|La cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|`DDP_Check`|Una casilla de verificación con una propiedad de control.|
|`DDP_LBIndex`|El índice de la cadena seleccionada en un cuadro de lista con una propiedad de control.|
|`DDP_LBString`|La cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras que el valor de la propiedad, pero no es necesario que coincida completamente.|
|`DDP_LBStringExact`|La cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|
|`DDP_Radio`|Un botón de opción con una propiedad de control.|
|`DDP_Text`|Texto con una propiedad de control.|

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage (clase)](../mfc/reference/colepropertypage-class.md)
