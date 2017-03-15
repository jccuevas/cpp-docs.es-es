---
title: "Tutorial: Agregar animaci&#243;n a un proyecto de MFC | Microsoft Docs"
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
  - "animación [MFC]"
  - "MFC, animación"
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Tutorial: Agregar animaci&#243;n a un proyecto de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial se enseña cómo agregar un objeto animado básico a un proyecto de Visual C\+\+, biblioteca MFC \(Microsoft Foundation Class\).  
  
 El tutorial muestra cómo llevar a cabo estas tareas:  
  
-   Crear una aplicación de MFC.  
  
-   Agregar un menú y después agregar comandos para iniciar y detener una animación.  
  
-   Crear los controladores para los comandos de inicio y parada.  
  
-   Agregar un objeto animado al proyecto.  
  
-   Centrar el objeto animado en la ventana.  
  
-   Comprobar los resultados.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## Requisitos previos  
 Para completar este tutorial, debe tener Visual Studio.  
  
### Para crear una aplicación de MFC  
  
1.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el panel de la izquierda bajo **Plantillas instaladas**, expanda **Visual C\+\+** y seleccione **MFC**.  En el panel central, seleccione **Aplicación MFC**.  En el cuadro **Nombre**, escriba `MFCAnimationWalkthrough`.  Haga clic en **Aceptar**.  
  
3.  En el cuadro de diálogo **Asistente para aplicaciones MFC**, compruebe que **Tipo de aplicación** es **Varios documentos**, **Estilo del proyecto** es **Visual Studio** y la opción **Compatibilidad con la arquitectura documento\/vista** está seleccionada.  Haga clic en **Finalizar**.  
  
### Para agregar un menú y después agregar comandos para iniciar y detener una animación  
  
1.  En el menú **Ver**, elija **Otras ventanas** y, a continuación, haga clic en **Vista de recursos**.  
  
2.  En **Vista de recursos**, vaya a la carpeta **Menú** y ábrala.  Haga doble clic en el recurso `IDR_MFCAnimationWalTYPE` para abrirlo y modificarlo.  
  
3.  En la barra de menús, en el cuadro de **Escriba aquí** , `T&nimation` tipo para crear un menú de animación.  
  
4.  En **Animación**, en el cuadro de **Escriba aquí** , `Comienzo &Adelante` tipo para crear un comando de inicio hacia delante.  
  
5.  En **Inicio hacia delante**, en el cuadro de **Escriba aquí** , `Comienzo &Hacia atrás`escrito.  
  
6.  En **Inicio hacia atrás**, en el cuadro de **Escriba aquí** , `S&arriba` tipo para crear un comando de detención.  
  
7.  Guarde MFCAnimationWalkthrough.rc y ciérrelo.  
  
8.  En el **Explorador de soluciones**, haga doble clic en MainFrm.cpp para abrirlo y modificarlo.  En el método `CMainFrame::OnCreate`, busque la sección que tiene varias llamadas a `lstBasicCommands.AddTail`.  Justo después de esa sección, agregue el siguiente código.  
  
    ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);  
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);  
    ```  
  
9. Guarde el archivo y ciérrelo.  
  
### Para crear los controladores para los comandos de inicio y parada  
  
1.  En el menú **Proyecto**, haga clic en **Asistente para clases**.  
  
2.  En el **Asistente para clases MFC**, en **Nombre de clase**, seleccione `CMFCAnimationWalkthroughView`.  
  
3.  En la pestaña **Comandos**, en el cuadro **Identificadores de objeto**, seleccione `ID_ANIMATION_STARTFORWARD` y, a continuación, en el cuadro **Mensajes**, seleccione `COMMAND`.  Haga clic en **Agregar controlador**.  
  
4.  Haga clic en **Aceptar** en el cuadro de diálogo **Agregar función de miembro**.  
  
5.  En el cuadro **Identificadores de objeto**, seleccione `ID_ANIMATION_STARTBACKWARD` y, a continuación, en el cuadro **Mensajes**, seleccione `COMMAND`.  Haga clic en **Agregar controlador**.  
  
6.  Haga clic en **Aceptar** en el cuadro de diálogo **Agregar función de miembro**.  
  
7.  En el cuadro **Identificadores de objeto**, seleccione `ID_ANIMATION_STOP` y, a continuación, en el cuadro **Mensajes**, seleccione `COMMAND`.  Haga clic en **Agregar controlador** y, a continuación, haga clic en **Aceptar**.  
  
8.  Haga clic en **Aceptar** en el cuadro de diálogo **Agregar función de miembro**.  
  
9. En **Asistente para clases MFC**, haga clic en **Aceptar**.  
  
10. Guarde MFCAnimationWalkthroughView.cpp, que está abierto en el editor, pero no lo cierre.  
  
### Par agregar un objeto animado al proyecto  
  
1.  En el Explorador de soluciones, haga doble clic en MFCAnimationWalkthroughView.h para abrirlo y modificarlo.  Justo antes de la definición de la clase `CMFCAnimationWalkthroughView`, agregue el siguiente código para crear un controlador de animación personalizado que administrará los conflictos de programación con el objeto de animación.  
  
    ```  
    class CCustomAnimationController : public CAnimationController  
    {  
    public:  
        CCustomAnimationController()  
        {  
        }  
  
        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled, CAnimationGroup* pGroupNew, UI_ANIMATION_PRIORITY_EFFECT priorityEffect)  
        {  
            return TRUE;  
        }  
    };  
    ```  
  
2.  Al final de la clase `CMFCAnimationWalkthroughView`, agregue el código siguiente.  
  
    ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
    ```  
  
3.  Después de la línea `DECLARE_MESSAGE_MAP()`, agregue el código siguiente.  
  
    ```  
    void Animate(BOOL bDirection);  
    ```  
  
4.  Guarde el archivo y ciérrelo.  
  
5.  En MFCAnimationWalkthroughView.cpp, en la parte superior del archivo después de las instrucciones `#include` pero antes de cualquier método de clase, agregue el siguiente código.  
  
    ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
    ```  
  
6.  Al final del constructor para `CMFCAnimationWalkthroughView`, agregue el código siguiente.  
  
    ```  
    m_animationController.EnableAnimationTimerEventHandler();  
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);  
  
    m_animationColor = RGB(255, 255, 255);  
    m_animationRect = CRect(0, 0, 0, 0);  
  
    m_animationColor.SetID(-1, nAnimationGroup);  
    m_animationRect.SetID(-1, nAnimationGroup);  
  
    m_animationController.AddAnimationObject(&m_animationColor);  
    m_animationController.AddAnimationObject(&m_animationRect);  
    ```  
  
7.  Busque el método `CAnimationWalthroughView::PreCreateWindow` y, a continuación, reemplácelo por el código siguiente.  
  
    ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
    {  
        // TODO: Modify the Window class or styles here by modifying  
        //  the CREATESTRUCT cs  
  
        m_animationController.SetRelatedWnd(this);  
        return CView::PreCreateWindow(cs);  
    }  
    ```  
  
8.  Busque el método `CAnimationWalkthroughView::OnDraw` y, a continuación, reemplácelo por el código siguiente.  
  
    ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
    {  
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();  
        ASSERT_VALID(pDoc);  
        if (!pDoc)  
            return;  
  
        // TODO: add draw code for native data here  
        CMemDC dcMem(*pDC, this);  
        CDC& dc = dcMem.GetDC();  
  
        CRect rect;  
        GetClientRect(rect);  
  
        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));  
  
        CString strRGB;  
        strRGB.Format(_T("Fill Color is: %d; %d; %d"), GetRValue(m_animationColor), GetGValue(m_animationColor), GetBValue(m_animationColor));  
  
        dc.DrawText(strRGB, rect, DT_CENTER);  
        rect.top += nInfoAreaHeight;  
  
        CBrush br;  
  
        br.CreateSolidBrush(m_animationColor);  
        CBrush* pBrushOld = dc.SelectObject(&br);  
  
        dc.Rectangle((CRect)m_animationRect);  
        dc.SelectObject(pBrushOld);  
    }  
    ```  
  
9. Agregue el siguiente código al final del archivo.  
  
    ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
    {  
        static UI_ANIMATION_SECONDS duration = 3;  
        static DOUBLE dblSpeed = 35.;  
        static BYTE nStartColor = 50;  
        static BYTE nEndColor = 255;  
  
        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;  
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;  
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;  
  
        CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);  
        CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);  
        CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);  
  
        m_animationColor.AddTransition(pRedTransition, pGreenTransition, pBlueTransition);  
  
        CRect rectClient;  
        GetClientRect(rectClient);  
        rectClient.top += nInfoAreaHeight;  
  
        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;  
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;  
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;  
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;  
  
        CLinearTransition* pLeftTransition = new CLinearTransition(duration, nLeftFinal);  
        CLinearTransition* pTopTransition = new CLinearTransition(duration, nTopFinal);  
        CLinearTransition* pRightTransition = new CLinearTransition(duration, nRightFinal);  
        CLinearTransition* pBottomTransition = new CLinearTransition(duration, nBottomFinal);  
  
        m_animationRect.AddTransition(pLeftTransition, pTopTransition, pRightTransition, pBottomTransition);  
  
        CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();  
        CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup, pBlueTransition);  
  
        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
  
        m_animationController.AnimateGroup(nAnimationGroup);  
    }  
    ```  
  
10. En el menú **Proyecto**, haga clic en **Asistente para clases**.  
  
11. En el **Asistente para clases MFC**, en **Nombre de clase**, seleccione `CMFCAnimationWalkthroughView`.  
  
12. En la pestaña **Mensajes**, en el cuadro **Mensajes**, seleccione `WM_ERASEBKGND`, haga clic en **Agregar controlador** y, a continuación, en **Aceptar**.  
  
13. En MFCAnimationWalkthroughView.cpp, reemplace la implementación de `OnEraseBkgnd` por el siguiente código para reducir el parpadeo en el objeto animado cuando se dibuje de nuevo.  
  
    ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
    {  
        return TRUE;  
    }  
    ```  
  
14. Reemplace las implementaciones de `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward` y `CMFCAnimationWalkthroughView::OnAnimationStop` por el código siguiente.  
  
    ```  
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()  
    {  
        Animate(TRUE);  
    }  
  
    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()  
    {  
        Animate(FALSE);  
    }  
  
    void CMFCAnimationWalkthroughView::OnAnimationStop()  
    {  
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();  
        if (pManager != NULL)  
        {  
            pManager->AbandonAllStoryboards();  
        }  
    }  
  
    ```  
  
15. Guarde el archivo y ciérrelo.  
  
### Para centrar el objeto animado en la ventana  
  
1.  En el **Explorador de soluciones**, haga doble clic en MFCAnimationWalkthroughView.h para abrirlo y modificarlo.  Al final de la clase `CMFCAnimationWalkthroughView`, justo después de la definición de `m_animationRect` agregue el código siguiente.  
  
    ```  
    BOOL m_bCurrentDirection;  
    ```  
  
2.  Guarde el archivo y ciérrelo.  
  
3.  En el menú **Proyecto**, haga clic en **Asistente para clases**.  
  
4.  En el **Asistente para clases MFC**, en **Nombre de clase**, seleccione `CMFCAnimationWalkthroughView`.  
  
5.  En la pestaña **Mensajes**, en el cuadro **Mensajes**, seleccione `WM_SIZE`, haga clic en **Agregar controlador** y, a continuación, en **Aceptar**.  
  
6.  En MFCAnimationWalkthroughView.cpp, reemplace el código de `CMFCAnimationWalkthroughView::OnSize` por el siguiente.  
  
    ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);  
  
        CRect rect;  
        GetClientRect(rect);  
        rect.top += nInfoAreaHeight;  
  
        CRect rectAnim = m_animationRect;  
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,   
                                rect.CenterPoint().y - rectAnim.Height() / 2),   
                                rectAnim.Size());  
  
        if (m_animationController.IsAnimationInProgress())  
        {  
            Animate(m_bCurrentDirection);  
        }  
    }  
    ```  
  
7.  Al comienzo del constructor de `CMFCAnimationWalkthroughView`, agregue el código siguiente.  
  
    ```  
    m_bCurrentDirection = TRUE;  
    ```  
  
8.  Agregue el siguiente código al comienzo del método `CMFCAnimationWalkthroughView::Animate`.  
  
    ```  
    m_bCurrentDirection = bDirection;  
    ```  
  
9. Guarde el archivo y ciérrelo.  
  
### Para comprobar los resultados  
  
1.  Compile y ejecute la aplicación.  En el menú **Animación**, haga clic en **Iniciar avance.** Debe aparecer un rectángulo y rellenarse el área interna.  Al hacer clic en **Iniciar retroceso**, la animación se reproduce hacia atrás y al hacer clic en **Detener**, se detiene.  El color de relleno del rectángulo debería cambiar cuando la animación progresa y el color actual se debe mostrar en la parte superior de la ventana de animación.  
  
## Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)