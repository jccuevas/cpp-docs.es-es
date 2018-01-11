---
title: "Controles ActiveX MFC: Páginas de propiedades | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dde35df301c34a6c3a29c48d5ad145681b64a72e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-property-pages"></a>Controles ActiveX MFC: Páginas de propiedades
Páginas de propiedades permiten que un usuario del control ActiveX ver y cambiar las propiedades del control ActiveX. Estas propiedades son accesibles mediante la invocación de un cuadro de diálogo de propiedades de control, que contiene uno o más páginas de propiedades que proporcionan una interfaz gráfica personalizada para ver y editar las propiedades del control.  
  
 Páginas de propiedades del control ActiveX se muestran de dos maneras:  
  
-   Al verbo de propiedades del control (**OLEIVERB_PROPERTIES**) es el control invoca, abre un cuadro de diálogo de propiedades modales que contiene páginas de propiedades del control.  
  
-   El contenedor puede mostrar su propio cuadro de diálogo no modal que muestra las páginas de propiedades del control seleccionado.  
  
 El cuadro de diálogo de propiedades (que se muestra en la figura siguiente) consta de un área para mostrar la página de propiedades actual, fichas para cambiar entre páginas de propiedades y una colección de botones que realizan tareas comunes como cerrar el cuadro de diálogo de la página de propiedad, Cancelar los cambios realizados o aplicar inmediatamente los cambios en el control ActiveX.  
  
 ![Cuadro de diálogo de propiedades de Circ3](../mfc/media/vc373i1.gif "vc373i1")  
Cuadro de diálogo de propiedades  
  
 En este artículo se trata temas relacionados con el uso de páginas de propiedades en un control ActiveX. Se incluyen los siguientes:  
  
-   [Implementación de la página de propiedades predeterminado para un control ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Agregar controles a una página de propiedades](#_core_adding_controls_to_a_property_page)  
  
-   [Personalizar la función DoDataExchange](#_core_customizing_the_dodataexchange_function)  
  
 Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:  
  
-   [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Para obtener información sobre el uso de hojas de propiedades en una aplicación MFC que no sea un control ActiveX, vea [hojas de propiedades](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a>Implementación de la página de propiedades predeterminadas  
 Si utiliza el Asistente para controles ActiveX para crear el proyecto de control, el Asistente para controles ActiveX proporciona una clase de página de propiedades predeterminado para el control derivado de [COlePropertyPage clase](../mfc/reference/colepropertypage-class.md). Inicialmente, esta página de propiedades está en blanco, pero puede agregar cualquier control de cuadro de diálogo o un conjunto de controles en él. Dado que el Asistente para controles ActiveX crea la clase de página de una sola propiedad de forma predeterminada, las clases de página de propiedades adicionales (también deriva `COlePropertyPage`) debe crearse con la vista de clases. Para obtener más información acerca de este procedimiento, consulte [controles ActiveX de MFC: agregar otra página de propiedades de personalizado](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implementar una propiedad de página (en este caso, el valor predeterminado) es un proceso de tres pasos:  
  
#### <a name="to-implement-a-property-page"></a>Para implementar una página de propiedades  
  
1.  Agregar un `COlePropertyPage`-clase derivada para el proyecto de control. Si el proyecto se creó mediante el Asistente para controles de ActiveX (como en este caso), la clase de página de propiedades predeterminado ya existe.  
  
2.  Utilice el editor de cuadro de diálogo para agregar los controles a la plantilla de la página de propiedades.  
  
3.  Personalizar la `DoDataExchange` función de la `COlePropertyPage`-clase derivada para intercambiar valores entre el control de la página de propiedad y el control ActiveX.  
  
 Por ejemplo, con fines de los procedimientos siguientes usar un control simple (denominado "Sample"). Ejemplo se creó mediante el Asistente para controles ActiveX y contiene sólo la propiedad estándar Caption.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a>Agregar controles a una página de propiedades  
  
#### <a name="to-add-controls-to-a-property-page"></a>Para agregar controles a una página de propiedades  
  
1.  Con el proyecto de control abierto, abra la vista de recursos.  
  
2.  Haga doble clic en el **diálogo** icono de directorio.  
  
3.  Abra la **IDD_PROPPAGE_SAMPLE** cuadro de diálogo.  
  
     El Asistente para controles ActiveX se anexa el nombre del proyecto al final del identificador de cuadro de diálogo, en este caso, ejemplo.  
  
4.  Arrastre y coloque el control seleccionado en el cuadro de herramientas en el área del cuadro de diálogo.  
  
5.  En este ejemplo, un texto con control de la etiqueta "Caption:" y un control de cuadro de edición con un **IDC_CAPTION** identificador son suficientes.  
  
6.  Haga clic en **guardar** en la barra de herramientas para guardar los cambios.  
  
 Ahora que se ha modificado la interfaz de usuario, debe vincular el cuadro de edición con la propiedad Caption. Esto se hace en la siguiente sección editando el `CSamplePropPage::DoDataExchange` función.  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a>Personalizar la función DoDataExchange  
 La página de propiedades [CWnd:: DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) función permite vincular valores de página de propiedad con los valores reales de las propiedades en el control. Para establecer vínculos, debe asignar los campos de la página de propiedades adecuado a sus respectivas propiedades del control.  
  
 Estas asignaciones se implementan utilizando la página de propiedades **DDP_** funciones. El **DDP_** funciona como el **DDX_** funciones utilizadas en los cuadros de diálogo estándar de MFC, con una excepción. Además de la referencia a una variable miembro, **DDP_** funciones toman el nombre de la propiedad de control. La siguiente es una entrada típica de la `DoDataExchange` función para una página de propiedades.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 Esta función asocia la página de propiedades `m_caption` variable de miembro con el título con el `DDP_TEXT` función.  
  
 Una vez que el control de la página de propiedades insertado, es necesario establecer un vínculo entre el control de la página de propiedades, `IDC_CAPTION`, y el uso de la propiedad del control real, título, el **DDP_Text** funcione como se describió anteriormente.  
  
 [Páginas de propiedades](../mfc/reference/property-pages-mfc.md) están disponibles para otros tipos de control de cuadro de diálogo, por ejemplo, casillas, botones de radio y cuadros de lista. La tabla siguiente muestra el conjunto completo de la página de propiedades **DDP_** funciones y sus fines:  
  
### <a name="property-page-functions"></a>Las funciones de la página de propiedades  
  
|Nombre de la función|Use esta función para vincular|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|Índice de la cadena seleccionada en un cuadro combinado con una propiedad de control.|  
|`DDP_CBString`|La cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras como valor de la propiedad, pero no necesita coincidir totalmente.|  
|`DDP_CBStringExact`|La cadena seleccionada en un cuadro combinado con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|  
|`DDP_Check`|Una casilla de verificación con una propiedad de control.|  
|`DDP_LBIndex`|Índice de la cadena seleccionada en un cuadro de lista con una propiedad de control.|  
|`DDP_LBString`|La cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada puede comenzar con las mismas letras como valor de la propiedad, pero no necesita coincidir totalmente.|  
|`DDP_LBStringExact`|La cadena seleccionada en un cuadro de lista con una propiedad de control. La cadena seleccionada y el valor de cadena de la propiedad deben coincidir exactamente.|  
|`DDP_Radio`|Un botón de opción con una propiedad de control.|  
|**DDP_TEXT**|Texto con una propiedad de control.|  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage (clase)](../mfc/reference/colepropertypage-class.md)
