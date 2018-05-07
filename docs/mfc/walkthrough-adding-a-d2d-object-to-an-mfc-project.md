---
title: 'Tutorial: Agregar objetos D2D a un proyecto MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7985b36c0eeaa7adf5441a7a6fbb3314bac8353f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Tutorial: Agregar objetos D2D a un proyecto de MFC
Este tutorial enseña a agregar un Direct2D básica (D2D) el objeto a Visual C++, el proyecto de biblioteca de clases de Microsoft Foundation (MFC) y, a continuación, compile el proyecto en una aplicación que imprime "Hello, world" sobre un fondo degradado.  
  
 El tutorial muestra cómo realizar estas tareas:  
  
-   Crear una aplicación MFC.  
  
-   Crear un pincel de color sólido y un pincel de degradado lineal.  
  
-   Modificar el pincel de degradado para que el cambio se realizará correctamente cuando se cambia el tamaño de la ventana.  
  
-   Implementar un controlador de dibujo D2D.  
  
-   Comprobar los resultados.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, debe tener Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>Para crear una aplicación MFC  
  
1.  En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, en el panel izquierdo bajo **plantillas instaladas**, expanda **Visual C++** y, a continuación, seleccione **MFC**. En el panel central, seleccione **aplicación MFC**. En el cuadro **Nombre**, escriba `MFCD2DWalkthrough`. Haga clic en **Aceptar**.  
  
3.  En el **Asistente para aplicaciones MFC**, haga clic en **finalizar** sin cambiar la configuración.  
  
### <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Para crear un pincel de color sólido y un pincel de degradado lineal  
  
1.  En **el Explorador de soluciones**, en la **MFCD2DWalkthrough** del proyecto, en la **archivos de encabezado** carpeta, abra MFCD2DWalkthroughView.h. Agregue el código siguiente a la `CMFCD2DWalkthroughView` clase para crear tres variables de datos.  
  
 ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
 ```  
  
     Guarde el archivo y ciérrelo.  
  
2.  En el **archivos de código fuente** carpeta, abra MFCD2DWalkthroughView.cpp. En el constructor para la `CMFCD2DWalkthroughView` de clases, agregue el código siguiente.  
  
 ''' * / / Habilitar la compatibilidad D2D con esta ventana:  
    EnableD2DSupport();

 * / / Inicializar D2D recursos:  
    m_pBlackBrush = CD2DSolidColorBrush(GetRenderTarget() nueva, D2D1::ColorF(D2D1::ColorF::Black));

 
    m_pTextFormat = nueva CD2DTextFormat(GetRenderTarget(), _T("Verdana"), 50);

    m_pTextFormat -> Get() -> SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);

 m_pTextFormat -> Get() -> SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

 
    D2D1_GRADIENT_STOP gradientStops [2].  
 
    gradientStops [0] .color = D2D1::ColorF(D2D1::ColorF::White);

    .position gradientStops [0] = 0.f;  
    gradientStops [1] .color = D2D1::ColorF(D2D1::ColorF::Indigo);

    .position gradientStops [1] = 1.f;  
 
    m_pLinearGradientBrush = CD2DLinearGradientBrush(GetRenderTarget() nuevo,   
    gradientStops, ARRAYSIZE(gradientStops),  
    D2D1::LinearGradientBrushProperties (D2D1::Point2F (0, 0), D2D1::Point2F (0, 0)));

 ```  
  
     Save the file and close it.  
  
### To modify the gradient brush so that it will change appropriately when the window is resized  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, in the **Messages** box, select `WM_SIZE` and then click **Add Handler**. This action adds the `OnSize` message handler to the `CMFCD2DWalkthroughView` class.  
  
4.  In the **Existing handlers** box, select `OnSize`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnSize` method. At the end of the method, add the following code.  
  
 ```  
    m_pLinearGradientBrush -> SetEndPoint (CPoint (cx, cy));

 ```  
  
     Save the file and close it.  
  
### To implement a D2D drawing handler  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, click **Add Custom Message**.  
  
4.  In the **Add Custom Message** dialog box, in the **Custom Windows Message** box, type `AFX_WM_DRAW2D`. In the **Message handler name** box, type `OnDraw2D`. Select the **Registered Message** option and then click **OK**. This action adds a message handler for the `AFX_WM_DRAW2D` message to the `CMFCD2DWalkthroughView` class.  
  
5.  In the **Existing handlers** box, select `OnDraw2D`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnDraw2D` method. Use the following code for the `CMFCD2DWalkthroughView::OnDrawD2D` method.  
  
 ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
 PRenderTarget CHwndRenderTarget * = (CHwndRenderTarget *) lParam;  
    ASSERT_VALID(pRenderTarget);

 
    CRect rect;  
    GetClientRect(rect);

 
    pRenderTarget -> FillRectangle (rect, m_pLinearGradientBrush);

    pRenderTarget -> DrawText (_T ("Hello, World!"), rect, m_pBlackBrush, m_pTextFormat);

 
    Devuelve TRUE;  
 }  
 ```  
  
     Save the file and close it.  
  
### To verify the results  
  
1.  Build and run the application. It should have a gradient rectangle that changes when you resize the window. “Hello World!” should be displayed in the center of the rectangle.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)

