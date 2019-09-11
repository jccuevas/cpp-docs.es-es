---
title: 'Controles ActiveX MFC: Agregar otra página de propiedades personalizada'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 09d85d69efc4c6cf0bf253099bae78c1e570f8a5
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907382"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Controles ActiveX MFC: Agregar otra página de propiedades personalizada

En ocasiones, un control ActiveX tendrá más propiedades de las que pueden caber en una página de propiedades. En este caso, puede agregar páginas de propiedades al control ActiveX para mostrar estas propiedades.

En este artículo se explica cómo agregar nuevas páginas de propiedades a un control ActiveX que ya tiene al menos una página de propiedades. Para obtener más información sobre cómo agregar páginas de propiedades estándar (fuente, imagen o color), vea [el artículo controles ActiveX de MFC: Usar páginas](../mfc/mfc-activex-controls-using-stock-property-pages.md)de propiedades estándar.

En los procedimientos siguientes se usa un marco de control ActiveX de ejemplo creado por el Asistente para controles ActiveX. Por lo tanto, los nombres y los identificadores de clase son únicos en este ejemplo.

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:

- [Controles ActiveX de MFC: páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)

- [Controles ActiveX de MFC: usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Se recomienda encarecidamente que las nuevas páginas de propiedades se adhieren al estándar de tamaño para las páginas de propiedades de controles ActiveX. Las páginas de propiedades de color y imagen estándar miden las unidades de cuadro de diálogo 250x62 (DLU). La página de propiedades de fuente estándar es 250x110 DLU. La página de propiedades predeterminada creada por el Asistente para controles ActiveX utiliza el estándar 250x62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Para insertar una nueva plantilla de página de propiedades en el proyecto

1. Con el proyecto de control abierto, abra Vista de recursos en el área de trabajo del proyecto.

1. Haga clic con el botón derecho en Vista de recursos para abrir el menú contextual y haga clic en **Agregar recurso**.

1. Expanda el nodo **cuadro de diálogo** y seleccione **IDD_OLE_PROPPAGE_SMALL**.

1. Haga clic en **nuevo** para agregar el recurso a su proyecto.

1. Seleccione la nueva plantilla de página de propiedades para actualizar la ventana **propiedades** (en **vista de recursos**).

1. Escriba un nuevo valor para la propiedad **ID** . En este ejemplo se usa **IDD_PROPPAGE_NEWPAGE**.

1. Haga clic en **Guardar** en la barra de herramientas.

### <a name="to-associate-the-new-template-with-a-class"></a>Para asociar la nueva plantilla a una clase

1. Abra Vista de clases.

1. Haga clic con el botón secundario en Vista de clases para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

   Se abrirá el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md) .

1. Haga doble clic en la plantilla **clase MFC** .

1. En el cuadro **nombre de clase** del [Asistente para clases MFC](../mfc/reference/mfc-add-class-wizard.md), escriba un nombre para la nueva clase de cuadro de diálogo. (En este ejemplo, `CAddtlPropPage`).

1. Si desea cambiar los nombres de archivo, haga clic en **cambiar**. Escriba los nombres de los archivos de implementación y de encabezado, o acepte los nombres predeterminados.

1. En el cuadro **clase base** , seleccione `COlePropertyPage`.

1. En el cuadro ID. de **diálogo** , seleccione **IDD_PROPPAGE_NEWPAGE**.

9. Haga clic en **Finalizar** para crear la clase.

Para permitir el acceso de los usuarios del control a esta nueva página de propiedades, realice los cambios siguientes en la sección macro IDs de la página de propiedades del control (ubicada en el archivo de implementación del control):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Tenga en cuenta que debe aumentar el segundo parámetro de la macro BEGIN_PROPPAGEIDS (el recuento de páginas de propiedades) de 1 a 2.

También debe modificar el archivo de implementación del control (. CPP) para incluir el encabezado (. H) de la nueva clase de página de propiedades.

El paso siguiente implica la creación de dos nuevos recursos de cadena que proporcionarán un nombre de tipo y un título para la nueva página de propiedades.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Para agregar nuevos recursos de cadena a una página de propiedades

1. Con el proyecto de control abierto, abra Vista de recursos.

1. Haga doble clic en la carpeta de la **tabla de cadenas** y, a continuación, haga doble clic en el recurso de tabla de cadenas existente al que desea agregar una cadena.

   Se abrirá la tabla de cadenas en una ventana.

1. Seleccione la línea en blanco al final de la tabla de cadenas y escriba el texto, o título, de la cadena: por ejemplo, "página de propiedades adicional".

   Se abrirá una página de **propiedades de cadena** que muestra cuadros de **título** y de **identificador** . El cuadro **título** contiene la cadena que ha escrito.

1. En el cuadro **ID** , seleccione o escriba un identificador para la cadena. Presione entrar cuando termine.

   En este ejemplo se usa **IDS_SAMPLE_ADDPAGE** para el nombre de tipo de la nueva página de propiedades.

1. Repita los pasos 3 y 4 con **IDS_SAMPLE_ADDPPG_CAPTION** para el identificador y "página de propiedades adicional" para el título.

1. En. Archivo CPP de la nueva clase de página de propiedades (en este `CAddtlPropPage`ejemplo,) `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` modifique para que [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass)pase IDS_SAMPLE_ADDPAGE, como en el ejemplo siguiente:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Modifique el constructor de `CAddtlPropPage` para que IDS_SAMPLE_ADDPPG_CAPTION se pase `COlePropertyPage` al constructor, como se indica a continuación:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Después de realizar las modificaciones necesarias, recompile el proyecto y use el contenedor de prueba para probar la nueva página de propiedades. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
