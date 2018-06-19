---
title: 'Controles ActiveX MFC: Agregar página de propiedades personalizadas otro | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a0e8713bc228e65cb06e58d7ccb5389f7366e76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350786"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Controles ActiveX MFC: Agregar otra página de propiedades personalizadas
En ocasiones, un control ActiveX tendrá más propiedades que cabe en una página de propiedades. En este caso, puede agregar páginas de propiedades para el control ActiveX para mostrar estas propiedades.  
  
 Este artículo describe cómo agregar nuevas páginas de propiedades a un control ActiveX que ya tiene al menos una página de propiedades. Para obtener más información sobre cómo agregar propiedades estándar páginas (fuente, imagen o color), vea el artículo [controles ActiveX MFC: utilizar páginas de propiedades de existencias](../mfc/mfc-activex-controls-using-stock-property-pages.md).  
  
 Los siguientes procedimientos utilizan un marco de control de ActiveX de ejemplo creado por el Asistente para controles ActiveX. Por lo tanto, los nombres de clase y los identificadores son únicos para este ejemplo.  
  
 Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:  
  
-   [Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  Se recomienda encarecidamente esa propiedad nuevas páginas respetar el tamaño estándar para páginas de propiedades del control ActiveX. La propiedad de imagen y el color estándar páginas unidades de medida 250 x 62 diálogo (DLU). La página de propiedades de fuente estándar es 250 x 110 DLU. La página de propiedades predeterminado creada por el Asistente para controles ActiveX utiliza el estándar de 250 x 62 DLU.  
  
### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Para insertar una nueva plantilla de página de propiedades en el proyecto  
  
1.  Con el proyecto de control abierto, abra Vista de recursos en el área de trabajo del proyecto.  
  
2.  Pulse el botón derecho en la vista de recursos para abrir el menú contextual y haga clic en **Agregar recurso**.  
  
3.  Expanda el **diálogo** nodo y seleccione **IDD_OLE_PROPPAGE_SMALL**.  
  
4.  Haga clic en `New` para agregar el recurso al proyecto.  
  
5.  Seleccione la nueva plantilla de página de propiedades para actualizar la ventana Propiedades.  
  
6.  Escriba un nuevo valor para el **identificador** propiedad. Este ejemplo se utiliza **IDD_PROPPAGE_NEWPAGE**.  
  
7.  Haga clic en **guardar** en la barra de herramientas.  
  
### <a name="to-associate-the-new-template-with-a-class"></a>Para asociar la nueva plantilla con una clase  
  
1.  Abra la vista de clases.  
  
2.  Haga clic en vista de clases para abrir el menú contextual.  
  
3.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.  
  
     Se abrirá la [Agregar clase](../ide/add-class-dialog-box.md) cuadro de diálogo.  
  
4.  Haga doble clic en el **clase MFC** plantilla.  
  
5.  En el **nombre de la clase** cuadro el [Asistente para clases MFC](../mfc/reference/mfc-add-class-wizard.md), escriba un nombre para la nueva clase de cuadro de diálogo. (En este ejemplo, `CAddtlPropPage`.)  
  
6.  Si desea cambiar los nombres de archivo, haga clic en **cambiar**. Escriba los nombres de los archivos de encabezado y de implementación o acepte los nombres predeterminados.  
  
7.  En el **una clase Base** cuadro, seleccione `COlePropertyPage`.  
  
8.  En el **Id. del cuadro de diálogo** cuadro, seleccione **IDD_PROPPAGE_NEWPAGE**.  
  
9. Haga clic en **finalizar** para crear la clase.  
  
 Para permitir que a los usuarios del control de acceso a esta nueva página de propiedades, realice los cambios siguientes a la sección del control propiedad página identificadores macro (que se encuentra en el archivo de implementación):  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 Tenga en cuenta que se debe incrementar el segundo parámetro de la `BEGIN_PROPPAGEIDS` macro (el recuento de páginas de propiedades) a partir de 1 a 2.  
  
 También debe modificar el archivo de implementación (. CPP) para incluir el encabezado (. (H) del archivo de la nueva clase de página de propiedades.  
  
 El siguiente paso implica la creación de dos nuevos recursos de cadena que proporcionan un nombre de tipo y un título para la nueva página de propiedades.  
  
#### <a name="to-add-new-string-resources-to-a-property-page"></a>Para agregar nuevos recursos de cadena a una página de propiedades  
  
1.  Con el proyecto de control abierto, abra la vista de recursos.  
  
2.  Haga doble clic en el **tabla de cadenas** carpeta y, a continuación, haga doble clic en recurso al que desea agregar una cadena de la tabla de la cadena existente.  
  
     Se abre la tabla de cadenas en una ventana.  
  
3.  Seleccione la línea en blanco al final de la tabla de cadenas y escriba el texto o el título de la cadena: por ejemplo, "página de propiedades adicional."  
  
     Se abrirá una **propiedades de la cadena** que muestra la página **título** y **identificador** cuadros. El **título** cuadro contiene la cadena que ha escrito.  
  
4.  En el **identificador** cuadro, seleccione o escriba un identificador de la cadena. Cuando haya terminado, presione ENTRAR.  
  
     Este ejemplo se utiliza **IDS_SAMPLE_ADDPAGE** para el nombre de tipo de la nueva página de propiedades.  
  
5.  Repita los pasos 3 y 4 con **IDS_SAMPLE_ADDPPG_CAPTION** para el identificador y "Página de propiedades adicional" para el título.  
  
6.  En. CPP de la nueva clase de página de propiedades (en este ejemplo, `CAddtlPropPage`) modificar el `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` para que se pasa IDS_SAMPLE_ADDPAGE por [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), como en el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  Modifique el constructor de `CAddtlPropPage` para que **IDS_SAMPLE_ADDPPG_CAPTION** se pasa a la `COlePropertyPage` constructor, como se indica a continuación:  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 Una vez realizadas las modificaciones necesarias Recompile el proyecto y utilice Test Container para probar la nueva página de propiedades. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

