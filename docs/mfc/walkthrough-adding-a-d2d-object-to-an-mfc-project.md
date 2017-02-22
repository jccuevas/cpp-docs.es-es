---
title: "Tutorial: Agregar objetos D2D a un proyecto de MFC | Microsoft Docs"
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
  - "D2D [MFC]"
  - "MFC, D2D"
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Tutorial: Agregar objetos D2D a un proyecto de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial se enseña a agregar un objeto Direct2D \(D2D\) básico a un proyecto de Visual C\+\+, de la biblioteca MFC \(Microsoft Foundation Class\) y, a continuación, compila el proyecto en una aplicación que imprime "Hello, world" en un fondo del degradado.  
  
 El tutorial muestra cómo llevar a cabo estas tareas:  
  
-   Crear una aplicación de MFC.  
  
-   Crear un pincel del color sólido y un pincel de degradado lineal.  
  
-   Modificar el pincel de degradado para que cambie cuando se cambia el tamaño de la ventana.  
  
-   Implementar un controlador de dibujo D2D.  
  
-   Comprobar los resultados.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## Requisitos previos  
 Para completar este tutorial, debe tener Visual Studio.  
  
### Para crear una aplicación de MFC  
  
1.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el panel de la izquierda bajo **Plantillas instaladas**, expanda **Visual C\+\+** y seleccione **MFC**.  En el panel central, seleccione **Aplicación MFC**.  En el cuadro **Nombre**, escriba `MFCD2DWalkthrough`.  Haga clic en **Aceptar**.  
  
3.  En el **Asistente para aplicaciones MFC**, haga clic en **Finalizar** sin cambiar ningún valor.  
  
### Para crear un pincel del color sólido y un pincel de degradado lineal  
  
1.  En el **Explorador de soluciones**, en el proyecto **MFCD2DWalkthrough**, en la carpeta **Archivos de encabezado**, abra MFCD2DWalkthroughView.h.  Agregue el siguiente código a la clase `CMFCD2DWalkthroughView` para crear tres variables de datos.  
  
    ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
    ```  
  
     Guarde el archivo y ciérrelo.  
  
2.  En la carpeta **Archivos de código fuente**, abra MFCD2DWalkthroughView.cpp.  En el constructor de la clase `CMFCD2DWalkthroughView`, agregue el código siguiente.  
  
    ```  
    // Enable D2D support for this window:  
    EnableD2DSupport();  
  
    // Initialize D2D resources:  
    m_pBlackBrush = new CD2DSolidColorBrush(GetRenderTarget(), D2D1::ColorF(D2D1::ColorF::Black));  
  
    m_pTextFormat = new CD2DTextFormat(GetRenderTarget(), _T("Verdana"), 50);  
    m_pTextFormat->Get()->SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);  
    m_pTextFormat->Get()->SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);  
  
    D2D1_GRADIENT_STOP gradientStops[2];  
  
    gradientStops[0].color = D2D1::ColorF(D2D1::ColorF::White);  
    gradientStops[0].position = 0.f;  
    gradientStops[1].color = D2D1::ColorF(D2D1::ColorF::Indigo);  
    gradientStops[1].position = 1.f;  
  
    m_pLinearGradientBrush = new CD2DLinearGradientBrush(GetRenderTarget(),   
        gradientStops, ARRAYSIZE(gradientStops),  
        D2D1::LinearGradientBrushProperties(D2D1::Point2F(0, 0), D2D1::Point2F(0, 0)));  
    ```  
  
     Guarde el archivo y ciérrelo.  
  
### Para modificar el pincel de degradado para que cambie cuando se modifica el tamaño de la ventana  
  
1.  En el menú **Proyecto**, haga clic en **Asistente para clases**.  
  
2.  En el **Asistente para clases MFC**, en **Nombre de clase**, seleccione `CMFCD2DWalkthroughView`.  
  
3.  En la pestaña **Mensajes**, en el cuadro **Mensajes**, seleccione `WM_SIZE`, haga clic en **Agregar controlador**.  Esta acción agrega el controlador de mensajes `OnSize` a la clase `CMFCD2DWalkthroughView`.  
  
4.  En el cuadro **Controladores existentes**, seleccione `OnSize`.  Haga clic en **Editar código** para mostrar el método `CMFCD2DWalkthroughView::OnSize`.  Agregue el siguiente código al final del método.  
  
    ```  
    m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));  
    ```  
  
     Guarde el archivo y ciérrelo.  
  
### Para implementar un controlador de dibujo D2D  
  
1.  En el menú **Proyecto**, haga clic en **Asistente para clases**.  
  
2.  En el **Asistente para clases MFC**, en **Nombre de clase**, seleccione `CMFCD2DWalkthroughView`.  
  
3.  En la pestaña **Mensajes**, haga clic en **Agregar mensaje personalizado**.  
  
4.  En el cuadro de diálogo **Agregar mensaje personalizado**, en el cuadro **Mensaje de Windows personalizado**, escriba `AFX_WM_DRAW2D`.  En el cuadro **Nombre del controlador de mensajes**, escriba `OnDraw2D`.  Seleccione la opción **Mensaje registrado** y, a continuación, haga clic en **Aceptar**.  Esta acción agrega el controlador de mensajes para el mensaje `AFX_WM_DRAW2D` a la clase `CMFCD2DWalkthroughView`.  
  
5.  En el cuadro **Controladores existentes**, seleccione `OnDraw2D`.  Haga clic en **Editar código** para mostrar el método `CMFCD2DWalkthroughView::OnDraw2D`.  Use el código siguiente para el método `CMFCD2DWalkthroughView::OnDrawD2D`:  
  
    ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
        CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;  
        ASSERT_VALID(pRenderTarget);  
  
        CRect rect;  
        GetClientRect(rect);  
  
        pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);  
        pRenderTarget->DrawText(_T("Hello, World!"), rect, m_pBlackBrush, m_pTextFormat);  
  
        return TRUE;  
    }  
    ```  
  
     Guarde el archivo y ciérrelo.  
  
### Para comprobar los resultados  
  
1.  Compile y ejecute la aplicación.  Debe tener un rectángulo de degradado que cambia cuando se cambia el tamaño de la ventana. "Hello World\!" debe aparecer en el centro del rectángulo.  
  
## Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)