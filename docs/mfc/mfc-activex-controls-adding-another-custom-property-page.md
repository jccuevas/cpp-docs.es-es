---
title: "Controles ActiveX MFC: Agregar otra p&#225;gina de propiedades personalizadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], páginas de propiedades"
  - "páginas de propiedades personalizadas"
  - "controles ActiveX en MFC [C++], páginas de propiedades"
  - "páginas de propiedades [C++], controles ActiveX en MFC"
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Agregar otra p&#225;gina de propiedades personalizadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En ocasiones, un control ActiveX tendrá más propiedades que puede razonablemente quepa en una página de propiedades.  En este caso, puede agregar páginas de propiedades al control ActiveX para mostrar estas propiedades.  
  
 En este artículo se abordan agregar nuevas páginas de propiedades a un control ActiveX que ya tiene por lo menos una página de propiedades.  Para obtener más información sobre las páginas de propiedades de la acción de suma \(fuente, imagen, o color\), vea el artículo [Controles ActiveX de MFC: Utilizando las páginas de propiedades comunes](../mfc/mfc-activex-controls-using-stock-property-pages.md).  
  
 Los procedimientos siguientes utilizan un marco del control ActiveX del ejemplo creado por el asistente para controles ActiveX.  Por consiguiente, los nombres de clase y los identificadores son únicos en este ejemplo.  
  
 Para obtener más información sobre cómo utilizar las páginas de propiedades de un control ActiveX, vea los artículos siguientes:  
  
-   [Controles ActiveX de MFC: Páginas de propiedades](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Controles ActiveX de MFC: Utilizando las páginas de propiedades comunes](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  Se recomienda encarecidamente que las nuevas páginas de propiedades se adhieren a la norma de tamaño de las páginas de propiedades del control ActiveX.  La imagen y páginas de propiedades de colores comunes medir unidades de cuadro de diálogo 250x62 \(DLU\).  La página de propiedades de fuente estándar es 250x110 DLU.  La página de propiedades predeterminada creada por el asistente para controles ActiveX utiliza el estándar de 250x62 DLU.  
  
### Para insertar una nueva plantilla de página de propiedades del proyecto  
  
1.  Con el proyecto de control abierta, abra la vista de recursos en el área de trabajo de un proyecto.  
  
2.  Haga clic con el botón secundario en la vista de recursos para abrir el menú contextual y haga clic en **Agregar recurso**.  
  
3.  Expanda el nodo de **Cuadro de diálogo** , y seleccione **IDD\_OLE\_PROPPAGE\_SMALL**.  
  
4.  Haga clic en `New` para agregar el recurso al proyecto.  
  
5.  Seleccione la nueva plantilla de página de propiedades para actualizar la ventana Propiedades.  
  
6.  Escriba un nuevo valor para la propiedad de **Id** .  Este ejemplo utiliza **IDD\_PROPPAGE\_NEWPAGE**.  
  
7.  En la barra de herramientas, haga clic en **Guardar**.  
  
### Para asociar la nueva plantilla con una clase  
  
1.  Vista abrir de la clase.  
  
2.  Haga clic con el botón secundario en la vista de clases para abrir el menú contextual.  
  
3.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
     Se abre el cuadro de diálogo de [Agregar clase](../ide/add-class-dialog-box.md) .  
  
4.  Haga doble clic en la plantilla de **Clase MFC** .  
  
5.  En el cuadro de **Nombre de clase** en [Asistente para clases MFC](../mfc/reference/mfc-add-class-wizard.md), escriba un nombre para la nueva clase de diálogo. \(En este ejemplo, `CAddtlPropPage`.\)  
  
6.  Si desea que los nombres de archivo de los cambios, haga clic en **Cambiar**.  Escriba los nombres para la implementación y los archivos de encabezado, o acepte los nombres predeterminados.  
  
7.  En el cuadro de **Clase base** , seleccione `COlePropertyPage`.  
  
8.  En el cuadro de **Identificador de cuadro de diálogo** , seleccione **IDD\_PROPPAGE\_NEWPAGE**.  
  
9. Haga clic en **Finalizar** para crear la clase.  
  
 Para permitir el acceso de los usuarios del control en esta nueva página de propiedades, realice los cambios siguientes a la sección de macro de los id. de la página de propiedades del control \(ubicada en el archivo de implementación del control\):  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 Observe que debe aumentar el segundo parámetro de la macro de `BEGIN_PROPPAGEIDS` \(el número\) de la página de propiedades comprendidos entre 1 y 2.  
  
 También debe modificar el archivo del archivo de implementación del control \(.CPP\) para incluir el encabezado \(. H\) archivo de la nueva clase de la página de propiedades.  
  
 El paso siguiente consiste en crear de dos nuevos recursos de cadena que proporcionan un nombre de tipo y una leyenda para la nueva página de propiedades.  
  
#### Para agregar nuevos recursos de cadena a una página de propiedades  
  
1.  Con el proyecto de control abierta, abra la vista de recursos.  
  
2.  Haga doble clic en la carpeta de **Tabla de cadenas** y haga doble clic en el recurso de la tabla de cadenas al que desea agregar una cadena.  
  
     Esto abre la tabla de cadenas en una ventana.  
  
3.  Seleccione la línea en blanco al final de la tabla de cadenas y escriba el texto, o la leyenda, string: por ejemplo, “página de propiedades adicional”.  
  
     Esto abre una página de **String Properties** que muestra **caption** y cuadros de **Id** .  El cuadro de **caption** contiene la cadena especificado.  
  
4.  En el cuadro de **Id** , seleccione o escriba un identificador para la cadena.  Presione Entrar cuando termine.  
  
     Este ejemplo utiliza **IDS\_SAMPLE\_ADDPAGE** para el nombre de tipo de la nueva página de propiedades.  
  
5.  Repita los pasos 3 y 4 utilizando **IDS\_SAMPLE\_ADDPPG\_CAPTION** para el identificador y la página adicional de la propiedad” para la leyenda.  
  
6.  En el archivo de .CPP de la nueva clase de la página de propiedades \(en este ejemplo, `CAddtlPropPage`\) modifique `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` de modo que IDS\_SAMPLE\_ADDPAGE se pasa por [AfxOleRegisterPropertyPageClass](../Topic/AfxOleRegisterPropertyPageClass.md), como en el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  Modifique el constructor de `CAddtlPropPage` para pasar **IDS\_SAMPLE\_ADDPPG\_CAPTION** al constructor de `COlePropertyPage` , como sigue:  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/CPP/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 Después de haber creado que las modificaciones necesarias recompilen el contenedor de prueba del uso de probar la nueva página de propiedades.  Vea [Probar propiedades y eventos con Test Container](../mfc/testing-properties-and-events-with-test-container.md) para obtener información sobre cómo tener acceso a Test Container.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)