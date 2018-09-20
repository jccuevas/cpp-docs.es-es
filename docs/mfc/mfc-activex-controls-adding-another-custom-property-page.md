---
title: 'Controles ActiveX MFC: Agregar página de propiedades personalizadas otro | Microsoft Docs'
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
ms.openlocfilehash: ce81436781a92c8d2c9156e1d1c02513c3816dc4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440061"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Controles ActiveX MFC: Agregar otra página de propiedades personalizadas

En ocasiones, un control ActiveX tendrá más propiedades que cabe en una página de propiedades. En este caso, puede agregar páginas de propiedades al control ActiveX para mostrar estas propiedades.

En este artículo explica cómo agregar nuevas páginas de propiedades a un control ActiveX que ya tiene al menos una página de propiedades. Para obtener más información sobre cómo agregar propiedades estándar páginas (fuente, imagen o color), consulte el artículo [controles ActiveX MFC: usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Los siguientes procedimientos utilizan un marco de control ActiveX de ejemplo creado por el Asistente para controles ActiveX. Por lo tanto, los nombres de clase y los identificadores son únicos para este ejemplo.

Para obtener más información sobre el uso de páginas de propiedades en un control ActiveX, vea los siguientes artículos:

- [Controles ActiveX MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)

- [Controles ActiveX MFC: Usar páginas de propiedades estándar](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Se recomienda encarecidamente esa propiedad nuevas páginas respetar el tamaño estándar para páginas de propiedades del control ActiveX. La propiedad de imagen y el color estándar páginas unidades de medida 250 x 62 cuadro de diálogo (DLU). La página de propiedades estándar fuente es 250 x 110 DLU. La página de propiedades predeterminado creada por el Asistente para controles ActiveX utiliza el estándar de 250 x 62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Para insertar una nueva plantilla de página de propiedades en el proyecto

1. Con el proyecto de control abierto, abra la vista de recursos en el área de trabajo del proyecto.

1. Haga clic en vista de recursos para abrir el menú contextual y haga clic en **Agregar recurso**.

1. Expanda el **diálogo** nodo y seleccione **IDD_OLE_PROPPAGE_SMALL**.

1. Haga clic en **New** para agregar el recurso al proyecto.

1. Seleccione la nueva plantilla de página de propiedades para actualizar la ventana Propiedades.

1. Escriba un nuevo valor para el **ID** propiedad. Este ejemplo se utiliza **IDD_PROPPAGE_NEWPAGE**.

1. Haga clic en **guardar** en la barra de herramientas.

### <a name="to-associate-the-new-template-with-a-class"></a>Para asociar la nueva plantilla con una clase

1. Abra la vista de clases.

1. Haga clic en la vista de clases para abrir el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.

     Se abrirá el [Agregar clase](../ide/add-class-dialog-box.md) cuadro de diálogo.

1. Haga doble clic en el **clase MFC** plantilla.

1. En el **nombre de la clase** cuadro el [Asistente para clases MFC](../mfc/reference/mfc-add-class-wizard.md), escriba un nombre para la nueva clase de cuadro de diálogo. (En este ejemplo, `CAddtlPropPage`.)

1. Si desea cambiar los nombres de archivo, haga clic en **cambiar**. Escriba los nombres de los archivos de encabezado e implementación o acepte los nombres predeterminados.

1. En el **clase Base** cuadro, seleccione `COlePropertyPage`.

1. En el **Id. del cuadro de diálogo** cuadro, seleccione **IDD_PROPPAGE_NEWPAGE**.

9. Haga clic en **finalizar** para crear la clase.

Para permitir que a los usuarios del control de acceso a esta nueva página de propiedades, realice los cambios siguientes en la sección del control propiedad página identificadores macro (ubicada en el archivo de implementación):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Tenga en cuenta que debe aumentar el segundo parámetro de la macro BEGIN_PROPPAGEIDS (el número de páginas de propiedades) de 1 a 2.

También debe modificar el archivo de implementación (. Archivo CPP) para incluir el encabezado (. H) archivo de de la nueva clase de página de propiedades.

El paso siguiente implica la creación de dos nuevos recursos de cadena que proporcionan un nombre de tipo y un título para la nueva página de propiedades.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Para agregar nuevos recursos de cadena a una página de propiedades

1. Con el proyecto de control abierto, abra la vista de recursos.

1. Haga doble clic en el **tabla de cadenas** carpeta y, a continuación, haga doble clic en recurso al que desea agregar una cadena de la tabla de la cadena existente.

     Esto abre la tabla de cadenas en una ventana.

1. Seleccione la línea en blanco al final de la tabla de cadenas y escriba el texto o el título de la cadena: por ejemplo, "página de propiedades adicional."

     Se abrirá un **las propiedades de cadena** que muestra la página **título** y **ID** cuadros. El **título** cuadro contiene la cadena que escribió.

1. En el **ID** cuadro, seleccione o escriba un identificador de la cadena. Presione ENTRAR cuando termine.

     Este ejemplo se utiliza **IDS_SAMPLE_ADDPAGE** para el nombre de tipo de la nueva página de propiedades.

1. Repita los pasos 3 y 4 con **IDS_SAMPLE_ADDPPG_CAPTION** para el identificador y la "Página de propiedades adicionales" para el título.

1. En. CPP de la nueva clase de página de propiedades (en este ejemplo, `CAddtlPropPage`) modificar el `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` para que se pase IDS_SAMPLE_ADDPAGE [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), como en el ejemplo siguiente:

     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Modifique el constructor de `CAddtlPropPage` poder IDS_SAMPLE_ADDPPG_CAPTION se pasa a la `COlePropertyPage` constructor, como se indica a continuación:

     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Una vez realizadas las modificaciones necesarias Recompile el proyecto y usar el contenedor de prueba para probar la nueva página de propiedades. Consulte [Probar propiedades y eventos con un contenedor de prueba](../mfc/testing-properties-and-events-with-test-container.md) para obtener información acerca de cómo acceder al contenedor de prueba.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

