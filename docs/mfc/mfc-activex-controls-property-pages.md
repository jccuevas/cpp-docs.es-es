---
title: "Controles ActiveX MFC: P&#225;ginas de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertyPageDialog (clase)"
  - "DDP_ functions"
  - "DoDataExchange (método)"
  - "controles ActiveX en MFC, propiedades"
  - "controles ActiveX en MFC, páginas de propiedades"
  - "OLEIVERB_PROPERTIES"
  - "páginas de propiedades, controles ActiveX en MFC"
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Controles ActiveX MFC: P&#225;ginas de propiedades
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las páginas de propiedades permiten al usuario de un control ActiveX ver y cambiar las propiedades del control ActiveX.  Para obtener acceso a estas propiedades, se invoca un cuadro de diálogo de propiedades del control, el cual contiene una o varias páginas de propiedades que proporcionan una interfaz gráfica personalizada para ver y editar las propiedades del control.  
  
 Las páginas de propiedades del control ActiveX se muestran de dos maneras:  
  
-   Cuando se invoca el verbo de las propiedades del control \(**OLEIVERB\_PROPERTIES**\), el control se abre un cuadro de diálogo de propiedades modal que contiene las páginas de propiedades del control.  
  
-   El contenedor puede mostrar su propio cuadro de diálogo no modal que muestra las páginas de propiedades del control seleccionado.  
  
 El cuadro de diálogo de propiedades \(que se muestra en la figura siguiente\) consta de un área para mostrar la página actual de la propiedad, pestañas para cambiar entre las páginas de propiedades, y una colección de botones que realicen tareas comunes como cerrar el diálogo de la página de propiedades, se cualquier cambio realizado, o inmediatamente aplicando los cambios al control ActiveX.  
  
 ![Cuadro de diálogo de propiedades de Circ3](../mfc/media/vc373i1.png "vc373I1")  
Cuadro de diálogo Propiedades  
  
 En este artículo se tratan los temas relacionados con las páginas de propiedades de un control ActiveX.  Se incluyen los siguientes:  
  
-   [Implementar la propiedad predeterminada de un control ActiveX](#_core_implementing_the_default_property_page)  
  
-   [Agregar controles a una página de propiedades](#_core_adding_controls_to_a_property_page)  
  
-   [Personalizar la función de DoDataExchange](#_core_customizing_the_dodataexchange_function)  
  
 Para obtener más información sobre cómo utilizar las páginas de propiedades de un control ActiveX, vea los artículos siguientes:  
  
-   [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 Para obtener información sobre cómo utilizar las hojas de propiedades en una aplicación MFC distinto de un control ActiveX, vea [Hojas de propiedades](../mfc/property-sheets-mfc.md).  
  
##  <a name="_core_implementing_the_default_property_page"></a> Implementar la página de propiedad predeterminada  
 Si utiliza el asistente para controles ActiveX para crear el proyecto de control, el asistente para controles ActiveX proporciona una clase de página de la propiedad predeterminada del control derivado de [COlePropertyPage Class](../mfc/reference/colepropertypage-class.md).  Inicialmente, esta página de propiedades está en blanco, pero puede agregar cualquier control de cuadro de diálogo o conjunto de controles al.  Dado que el asistente para controles ActiveX solo crea una clase de la página de propiedades de forma predeterminada, las clases adicionales de la página de propiedades \(también derivadas de `COlePropertyPage`\) se deben realizar utilizando la vista de clases.  Para obtener más información sobre este procedimiento, vea [Controles ActiveX MFC: Agregar otra página de propiedades personalizadas](../mfc/mfc-activex-controls-adding-another-custom-property-page.md).  
  
 Implementar una página de propiedades \(en este caso, el valor predeterminado\) es un proceso de tres\- paso:  
  
#### Para implementar una página de propiedades  
  
1.  Agregue `COlePropertyPage`\- clase derivada al proyecto de control.  Si el proyecto se creó mediante el asistente para controles ActiveX \(como en este caso\), la clase de página de la propiedad predeterminada ya existe.  
  
2.  Utilice el editor de cuadros de diálogo para agregar controles a la plantilla de página de propiedades.  
  
3.  Personalizar la función de `COlePropertyPage`\- clase derivada de `DoDataExchange` a los valores de intercambio entre el control de la página de propiedades y el control ActiveX.  
  
 Como las vistas, los procedimientos siguientes utilizan un control sencillo \(denominado “ejemplo”\).  El ejemplo se creó mediante el asistente para controles ActiveX y sólo contiene la propiedad caption común.  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> Agregar Controles a una página de propiedades  
  
#### Para agregar controles a una página de propiedades  
  
1.  Con el proyecto de control abierta, abra la vista de recursos.  
  
2.  Haga doble clic en el icono de directorio de **Cuadro de diálogo** .  
  
3.  Abra el cuadro de diálogo de **IDD\_PROPPAGE\_SAMPLE** .  
  
     El asistente para controles ActiveX anexa el nombre del proyecto al final del identificador de diálogo, en este caso, ejemplo.  
  
4.  Arrastrar y colocar el control seleccionado del cuadro de herramientas al área del cuadro de diálogo.  
  
5.  Para este ejemplo, la leyenda de un control label de texto “: ” y un control de cuadro de edición con un identificador de **IDC\_CAPTION** es suficiente.  
  
6.  Haga clic en **Guardar** en la barra de herramientas para guardar los cambios.  
  
 Ahora que se ha modificado la interfaz de usuario, debe enlazar el control de edición con la propiedad caption.  Esto se hace en la sección siguiente editando la función de `CSamplePropPage::DoDataExchange` .  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> Personalizar la función de DoDataExchange  
 La función de [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md) de la página de propiedades permite vincular valores de la página de propiedades con los valores reales de las propiedades del control.  Para establecer vínculos, debe asignar los campos correspondientes de la página de propiedades a sus propiedades respectivas del control.  
  
 Estas asignaciones se implementan utilizando las funciones de **DDP\_** de la página de propiedades.  Las funciones de **DDP\_** funcionan como las funciones de **DDX\_** utilizadas en los cuadros de diálogo estándar de MFC, con una excepción.  Además de la referencia a una variable miembro, las funciones de **DDP\_** toman el nombre de la propiedad del control.  A continuación se muestra una entrada típica en función de `DoDataExchange` para una página de propiedades.  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/CPP/mfc-activex-controls-property-pages_1.cpp)]  
  
 Esta función asociado a la variable miembro de `m_caption` de la página de propiedades al leyenda, mediante la función de `DDP_TEXT` .  
  
 Después de hacer el control de página de propiedades insertar, debe establecer un vínculo entre el control de página de propiedades, `IDC_CAPTION`, y la propiedad real del control, leyenda, mediante la función de **DDP\_Text** anteriormente descrita.  
  
 [Páginas de propiedades](../mfc/reference/property-pages-mfc.md) está disponible para otros tipos de controles de cuadro de diálogo, como casillas, botones de radio, y cuadros de lista.  La tabla siguiente enumera el conjunto completo de funciones de **DDP\_** de la página de propiedades y sus propósitos:  
  
### Funciones de página de propiedades  
  
|Nombre de la función|Utilice esta función para vincular|  
|--------------------------|----------------------------------------|  
|`DDP_CBIndex`|El índice seleccionado de la cadena en un cuadro combinado con una propiedad del control.|  
|`DDP_CBString`|La cadena seleccionado en un cuadro combinado con una propiedad del control.  La cadena seleccionado puede empezar con las mismas letras que el valor de propiedad pero no tiene que coincidir con él totalmente.|  
|`DDP_CBStringExact`|La cadena seleccionado en un cuadro combinado con una propiedad del control.  La cadena seleccionado y el valor de cadena de propiedad deben coincidir exactamente.|  
|`DDP_Check`|Una casilla con una propiedad del control.|  
|`DDP_LBIndex`|El índice seleccionado de la cadena en un cuadro de lista con una propiedad del control.|  
|`DDP_LBString`|La cadena seleccionado en un cuadro de lista con una propiedad del control.  La cadena seleccionado puede empezar con las mismas letras que el valor de propiedad pero no tiene que coincidir con él totalmente.|  
|`DDP_LBStringExact`|La cadena seleccionado en un cuadro de lista con una propiedad del control.  La cadena seleccionado y el valor de cadena de propiedad deben coincidir exactamente.|  
|`DDP_Radio`|Un botón de radio a una propiedad del control.|  
|**DDP\_Text**|Texto con una propiedad del control.|  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage Class](../mfc/reference/colepropertypage-class.md)