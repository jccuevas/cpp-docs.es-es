---
title: 'Controles ActiveX MFC: Agregar otra página de propiedades personalizadas'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364739"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Controles ActiveX MFC: Agregar otra página de propiedades personalizadas

Ocasionalmente, un control ActiveX tendrá más propiedades de las que caben razonablemente en una página de propiedades. En este caso, puede agregar páginas de propiedades al control ActiveX para mostrar estas propiedades.

En este artículo se describe cómo agregar nuevas páginas de propiedades a un control ActiveX que ya tiene al menos una página de propiedades. Para obtener más información sobre cómo agregar páginas de propiedades de stock (fuente, imagen o color), vea el artículo Controles ActiveX de [MFC: Uso](../mfc/mfc-activex-controls-using-stock-property-pages.md)de páginas de propiedades de stock .

Los procedimientos siguientes usan un marco de control ActiveX de ejemplo creado por el Asistente para controles ActiveX. Por lo tanto, los nombres de clase y los identificadores son únicos en este ejemplo.

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, consulte los artículos siguientes:

- [Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)

- [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Se recomienda encarecidamente que las nuevas páginas de propiedades se adhieran al estándar de tamaño para las páginas de propiedades de control ActiveX. Las páginas de propiedades de imagen y color de stock miden unidades de diálogo de 250x62 (DLU). La página de propiedades de fuente estándar es de 250x110 DCPU. La página de propiedades predeterminada creada por el Asistente para controles ActiveX utiliza el estándar DLU de 250x62.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Para insertar una nueva plantilla de página de propiedades en el proyecto

1. Con el proyecto de control abierto, abra vista de recursos en el área de trabajo del proyecto.

1. Haga clic con el botón derecho en vista de recursos para abrir el menú contextual y haga clic en **Agregar recurso**.

1. Expanda el nodo **Diálogo** y seleccione **IDD_OLE_PROPPAGE_SMALL**.

1. Haga clic en **Nuevo** para agregar el recurso al proyecto.

1. Seleccione la nueva plantilla de página de propiedades para actualizar la ventana **Propiedades** (en **la vista de**recursos ).

1. Escriba un nuevo valor para la propiedad **ID.** En este ejemplo se utiliza **IDD_PROPPAGE_NEWPAGE**.

1. Haga clic en **Guardar** en la barra de herramientas.

### <a name="to-associate-the-new-template-with-a-class"></a>Para asociar la nueva plantilla con una clase

1. Abra la vista de clases.

1. Haga clic con el botón derecho en la Vista de clases para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

   Se abrirá el cuadro de diálogo [Agregar clase.](../ide/add-class-dialog-box.md)

1. Haga doble clic en la plantilla **Clase MFC.**

1. En el cuadro Nombre de **clase** del [Asistente para clases MFC](../mfc/reference/mfc-add-class-wizard.md), escriba un nombre para la nueva clase de cuadro de diálogo. (En este `CAddtlPropPage`ejemplo, .)

1. Si desea cambiar los nombres de archivo, haga clic en **Cambiar**. Escriba los nombres de los archivos de implementación y encabezado, o acepte los nombres predeterminados.

1. En el cuadro Clase `COlePropertyPage` **base,** seleccione .

1. En el cuadro ID de cuadro de **diálogo,** seleccione **IDD_PROPPAGE_NEWPAGE**.

1. Haga clic en **Finalizar** para crear la clase.

Para permitir que los usuarios del control accedan a esta nueva página de propiedades, realice los siguientes cambios en la sección de macros de ID de página de propiedades del control (ubicada en el archivo de implementación del control):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Tenga en cuenta que debe aumentar el segundo parámetro de la macro BEGIN_PROPPAGEIDS (el recuento de páginas de propiedades) de 1 a 2.

También debe modificar el archivo de implementación del control (. CPP) para incluir el encabezado (. H) de la nueva clase de página de propiedades.

El siguiente paso implica la creación de dos nuevos recursos de cadena que proporcionarán un nombre de tipo y un título para la nueva página de propiedades.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Para agregar nuevos recursos de cadena a una página de propiedades

1. Con el proyecto de control abierto, abra la vista de recursos.

1. Haga doble clic en la carpeta **Tabla** de cadenas y, a continuación, haga doble clic en el recurso de tabla de cadenas existente al que desea agregar una cadena.

   Esto abre la tabla de cadenas en una ventana.

1. Seleccione la línea en blanco al final de la tabla de cadenas y escriba el texto, o título, de la cadena: por ejemplo, "Página de propiedades adicionales."

   Se abrirá una página Propiedades de **cadena** que muestra los cuadros **Subtítulo** e **ID.** El cuadro **Título** contiene la cadena que ha escrito.

1. En el cuadro **ID,** seleccione o escriba un identificador para la cadena. Pulse Intro cuando termine.

   En este ejemplo se usa **IDS_SAMPLE_ADDPAGE** para el nombre de tipo de la nueva página de propiedades.

1. Repita los pasos 3 y 4 con **IDS_SAMPLE_ADDPPG_CAPTION** para el identificador y la "página de propiedades adicionales" para el título.

1. En. CPP de la nueva clase de página `CAddtlPropPage`de `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` propiedades (en este ejemplo, ) modifica el modo que ala IDS_SAMPLE_ADDPAGE [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), como en el ejemplo siguiente:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Modifique el `CAddtlPropPage` constructor de para que `COlePropertyPage` IDS_SAMPLE_ADDPPG_CAPTION se pase al constructor, como se indica a continuación:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Después de realizar las modificaciones necesarias, vuelva a generar el proyecto y use contenedor de pruebas para probar la nueva página de propiedades. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
