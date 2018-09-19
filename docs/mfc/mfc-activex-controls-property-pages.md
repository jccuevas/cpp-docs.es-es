---
title: 'Controles ActiveX MFC: Páginas de propiedades | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4d61c1b0d7fb7174bdf7df0c811b0159ece02d
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535243"
---
# <a name="mfc-activex-controls-property-pages"></a>Controles ActiveX MFC: Páginas de propiedades
Páginas de propiedades permiten que el usuario de un control ActiveX ver y cambiar las propiedades de controles ActiveX. Estas propiedades son accesibles mediante la invocación de un cuadro de diálogo Propiedades de control, que contiene uno o más páginas de propiedades que proporcionan una interfaz gráfica personalizada para ver y editar las propiedades del control.  

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).
  
 Páginas de propiedades del control ActiveX se muestran de dos maneras:  
  
-   Al verbo de propiedades del control (**OLEIVERB_PROPERTIES**) es invoca, el control abre un cuadro de diálogo de propiedades modal que contiene páginas de propiedades del control.  
  
-   El contenedor puede mostrar su propio cuadro de diálogo no modal que muestra las páginas de propiedades del control seleccionado.  
  
 El cuadro de diálogo de propiedades (que se muestra en la ilustración siguiente) consta de un área para mostrar la página de propiedades actual, las pestañas para cambiar entre páginas de propiedades y una colección de botones que realizan tareas comunes como cerrar el cuadro de diálogo de la página de propiedad, Cancelar los cambios realizados o aplicar inmediatamente los cambios en el control ActiveX.  
  
 ![Cuadro de diálogo Propiedades de Circ3](../mfc/media/vc373i1.gif "vc373i1")  
Cuadro de diálogo Propiedades  
  
 En este artículo se trata temas relacionados con el uso de páginas de propiedades en un control ActiveX. Se incluyen los siguientes:  
  
-   [Implementación de la página de propiedades predeterminado para un control ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Agregar controles a una página de propiedades](#_core_adding_controls_to_a_property_page)  
  
-   [Personalización de la función DoDataExchange](#_core_customizing_the_dodataexchange_function)  
  
 Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:  
  
-   [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Para obtener información sobre el uso de hojas de propiedades en una aplicación MFC que no sea un control ActiveX, vea [hojas de propiedades](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a> Implementación de la página de propiedades predeterminada  
 Si usa el Asistente para controles ActiveX para crear el proyecto de control, el Asistente para controles ActiveX proporciona una clase de página de propiedades predeterminado para el control derivado de [COlePropertyPage (clase)](../mfc/reference/colepropertypage-class.md). Inicialmente, esta página de propiedades está en blanco, pero puede agregar cualquier control de cuadro de diálogo o un conjunto de controles a él. Dado que el Asistente para controles ActiveX crea la clase de página de una sola propiedad de forma predeterminada, las clases de página de propiedades adicionales (también derivada de `COlePropertyPage`) debe crearse con la vista de clases. Para obtener más información sobre este procedimiento, consulte [controles ActiveX MFC: agregar otra página de propiedades de Custom](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implementar una propiedad de página (en este caso, el valor predeterminado) es un proceso de tres pasos:  
  
#### <a name="to-implement-a-property-page"></a>Para implementar una página de propiedades  
  
1.  Agregar un `COlePropertyPage`-clase derivada para el proyecto de control. Si el proyecto se creó mediante el Asistente para controles de ActiveX (como en este caso), la clase de página de propiedades predeterminada ya existe.  
  
2.  Utilice el editor de cuadro de diálogo para agregar los controles a la plantilla de página de propiedades.  
  
3.  Personalizar el `DoDataExchange` función de la `COlePropertyPage`-clase derivada para intercambiar valores entre el control de página de propiedades y el control ActiveX.  
  
 Por ejemplo, efectos, los procedimientos siguientes usar un control simple (denominado "Sample"). Ejemplo se creó mediante el Asistente para controles ActiveX y contiene sólo la propiedad Caption de cotizaciones.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> Agregar controles a una página de propiedades  
  
#### <a name="to-add-controls-to-a-property-page"></a>Para agregar controles a una página de propiedades  
  
1.  Con el proyecto de control abierto, abra la vista de recursos.  
  
2.  Haga doble clic en el **diálogo** icono de directorio.  
  
3.  Abra el cuadro de diálogo IDD_PROPPAGE_SAMPLE.  
  
     El Asistente para controles ActiveX se anexa el nombre del proyecto hasta el final del identificador de diálogo, en este caso, ejemplo.  
  
4.  Arrastre y coloque el control seleccionado en el cuadro de herramientas en el área del cuadro de diálogo.  
  
5.  En este ejemplo, un texto de control de etiqueta "Caption:" y un control de cuadro de edición con un identificador IDC_CAPTION son suficientes.  
  
6.  Haga clic en **guardar** en la barra de herramientas para guardar los cambios.  
  
 Ahora que se ha modificado la interfaz de usuario, debe vincular el cuadro de edición con la propiedad Caption. Esto se hace en la siguiente sección editando el `CSamplePropPage::DoDataExchange` función.  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> Personalización de la función DoDataExchange  
 La página de propiedades [CWnd:: DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) función le permite vincular valores de propiedad de página con los valores reales de las propiedades del control. Para establecer vínculos, debe asignar los campos de la página de propiedades adecuado para sus respectivas propiedades del control.  
  
 Estas asignaciones se implementan mediante la página de propiedades **DDP_** funciones. El **DDP_** funciones funcionan como el **DDX_** funciones utilizadas en cuadros de diálogo MFC estándar, con una excepción. Además de la referencia a una variable miembro, **DDP_** funciones toman el nombre de propiedad del control. El siguiente es una entrada típica en el `DoDataExchange` función para una página de propiedades.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Esta función asocia la página de propiedades *m_caption* variable miembro con el título, utilizando el `DDP_TEXT` función.  
  
 Una vez que el control de página de propiedad insertado, es necesario establecer un vínculo entre el control de página de propiedades, IDC_CAPTION y la propiedad del control real, Caption, mediante la `DDP_Text` funcione como se describió anteriormente.  
  
 [Páginas de propiedades](../mfc/reference/property-pages-mfc.md) están disponibles para otros tipos de control de cuadro de diálogo, como casillas de verificación, botones de radio y cuadros de lista. La tabla siguiente muestra el conjunto completo de la página de propiedades **DDP_** funciones y sus fines:  
  
### <a name="property-page-functions"></a>Las funciones de la página de propiedades  
  
|Nombre de la función|Use esta función para vincular|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Índice de la cadena seleccionada en un cuadro combinado con una propiedad de control.|  
|`DDP_CBString`|La cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras como valor de la propiedad, pero no necesita coinciden plenamente.|  
|`DDP_CBStringExact`|La cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|  
|`DDP_Check`|Casilla de verificación con una propiedad de control.|  
|`DDP_LBIndex`|Índice de la cadena seleccionada en un cuadro de lista con una propiedad de control.|  
|`DDP_LBString`|La cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras como valor de la propiedad, pero no necesita coinciden plenamente.|  
|`DDP_LBStringExact`|La cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|  
|`DDP_Radio`|Botón de radio con una propiedad de control.|  
|`DDP_Text`|Texto con una propiedad de control.|  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage (clase)](../mfc/reference/colepropertypage-class.md)
