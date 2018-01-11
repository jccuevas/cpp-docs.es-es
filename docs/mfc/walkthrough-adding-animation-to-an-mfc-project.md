---
title: "Tutorial: Agregar animación a un proyecto MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f027da0e90bc8dde015c2d42bd72ceb388aa0bba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>Tutorial: Agregar animación a un proyecto de MFC
Este tutorial le enseña cómo agregar un objeto animado básico a Visual C++, el proyecto de biblioteca de clase (MFC) de Microsoft Foundation.  
  
 El tutorial muestra cómo realizar estas tareas:  
  
-   Crear una aplicación MFC.  
  
-   Agregar un menú y, a continuación, agregar comandos para iniciar y detener una animación.  
  
-   Crear controladores para los comandos de inicio y detención.  
  
-   Agregue un objeto animado al proyecto.  
  
-   Centre el objeto animado en la ventana.  
  
-   Comprobar los resultados.  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, debe tener Visual Studio.  
  
### <a name="to-create-an-mfc-application"></a>Para crear una aplicación MFC  
  
1.  En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, en el panel izquierdo bajo **plantillas instaladas**, expanda **Visual C++** y, a continuación, seleccione **MFC**. En el panel central, seleccione **aplicación MFC**. En el cuadro **Nombre**, escriba `MFCAnimationWalkthrough`. Haga clic en **Aceptar**.  
  
3.  En el **Asistente para aplicaciones MFC** diálogo cuadro, compruebe que **tipo de aplicación** es **varios documentos**, **estilo del proyecto** es  **Visual Studio**y el **compatibilidad con la arquitectura documento/vista** opción está seleccionada. Haga clic en **Finalizar**.  
  
### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>Para agregar un menú y, a continuación, agregar comandos para iniciar y detener una animación  
  
1.  En el **vista** menú, elija **otras ventanas** y, a continuación, haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, navegue hasta la **menú** carpeta y ábralo. Haga doble clic en el `IDR_MFCAnimationWalTYPE` recurso para abrirlo para modificarlo.  
  
3.  En la barra de menús, en la **escriba aquí** , escriba `A&nimation` para crear un menú de animación.  
  
4.  En **animación**, en la **escriba aquí** , escriba `Start &Forward` para crear un comando de inicio al día.  
  
5.  En **iniciar al día**, en la **escriba aquí** , escriba `Start &Backward`.  
  
6.  En **iniciar con versiones anteriores**, en la **escriba aquí** , escriba `S&top` para crear un comando de detención.  
  
7.  Guardar MFCAnimationWalkthrough.rc y ciérrelo.  
  
8.  En **el Explorador de soluciones**, haga doble clic en MainFrm.cpp para abrirlo para modificarlo. En el `CMainFrame::OnCreate` método, busque la sección que tiene varias llamadas a `lstBasicCommands.AddTail`. Justo después de esa sección, agregue el código siguiente.  
  
 ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);

 lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);

    lstBasicCommands.AddTail(ID_ANIMATION_STOP);

 ```  
  
9. Guarde el archivo y ciérrelo.  
  
### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>Para crear controladores para el inicio y detener comandos  
  
1.  En el **proyecto** menú, haga clic en **Asistente para clases**.  
  
2.  En el **Asistente para clases MFC**, en **nombre de la clase**, seleccione `CMFCAnimationWalkthroughView`.  
  
3.  En el **comandos** ficha la **identificadores de objeto** cuadro, seleccione `ID_ANIMATION_STARTFORWARD`y, a continuación, en la **mensajes** cuadro, seleccione `COMMAND`. Haga clic en **Agregar controlador**.  
  
4.  En el **Agregar función de miembro** cuadro de diálogo, haga clic en **Aceptar**.  
  
5.  En el **identificadores de objeto** cuadro, seleccione `ID_ANIMATION_STARTBACKWARD`y, a continuación, en la **mensajes** cuadro, seleccione `COMMAND`. Haga clic en **Agregar controlador**.  
  
6.  En el **Agregar función de miembro** cuadro de diálogo, haga clic en **Aceptar**.  
  
7.  En el **identificadores de objeto** cuadro, seleccione `ID_ANIMATION_STOP`y, a continuación, en la **mensajes** cuadro, seleccione `COMMAND`. Haga clic en **Agregar controlador** y, a continuación, haga clic en **Aceptar**.  
  
8.  En el **Agregar función de miembro** cuadro de diálogo, haga clic en **Aceptar**.  
  
9. En el **Asistente para clases MFC**, haga clic en **Aceptar**.  
  
10. Guardar MFCAnimationWalkthroughView.cpp, que está abierto en el editor, pero no lo cierre.  
  
### <a name="to-add-an-animated-object-to-the-project"></a>Para agregar un objeto animado al proyecto  
  
1.  En el Explorador de soluciones, haga doble clic en MFCAnimationWalkthroughView.h para abrirlo para modificarlo. Justo antes de la definición de la `CMFCAnimationWalkthroughView` de clases, agregue el código siguiente para crear un controlador de animación personalizado que va a controlar conflictos de programación con el objeto de animación.  
  
 ```  
    class CCustomAnimationController : public CAnimationController  
 {  
    public: 
    CCustomAnimationController() 
 {  
 }  
 
    virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect)  
 {  
    return TRUE;  
 }  
 };  
 ```  
  
2.  Al final de la `CMFCAnimationWalkthroughView` de clases, agregue el código siguiente.  
  
 ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
 ```  
  
3.  Después de la `DECLARE_MESSAGE_MAP()` línea, agregue el código siguiente.  
  
 ```  
    void Animate(BOOL bDirection);

 ```  
  
4.  Guarde el archivo y ciérrelo.  
  
5.  En MFCAnimationWalkthroughView.cpp, en la parte superior del archivo después de la `#include` instrucciones pero antes de cualquier clase métodos, agregan el código siguiente.  
  
 ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
 ```  
  
6.  Al final del constructor para `CMFCAnimationWalkthroughView`, agregue el código siguiente.  
  
 ```  
    m_animationController.EnableAnimationTimerEventHandler();
m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);

 
    m_animationColor = RGB(255,
    255,
    255);

    m_animationRect = CRect(0,
    0,
    0,
    0);

 
    m_animationColor.SetID(-1,
    nAnimationGroup);

    m_animationRect.SetID(-1,
    nAnimationGroup);

 
    m_animationController.AddAnimationObject(&m_animationColor);

 m_animationController.AddAnimationObject(&m_animationRect);

 ```  
  
7.  Busque la `CAnimationWalthroughView::PreCreateWindow` método y, a continuación, reemplácela por el código siguiente.  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
 { *// TODO: Modify the Window class or styles here by modifying *//  the CREATESTRUCT cs  
 
    m_animationController.SetRelatedWnd(this);

 return CView::PreCreateWindow(cs);

 }  
 ```  
  
8.  Busque la `CAnimationWalkthroughView::OnDraw` método y, a continuación, reemplácela por el código siguiente.  
  
 ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
 {  
    CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
ASSERT_VALID(pDoc);

 if (!pDoc)  
    return; 
 *// TODO: add draw code for native data here  
    CMemDC dcMem(*pDC,
    this);

    CDC& dc = dcMem.GetDC();

 
    CRect rect;  
    GetClientRect(rect);

 
    dc.FillSolidRect(rect,
    GetSysColor(COLOR_WINDOW));

 
    CString strRGB;  
    strRGB.Format(_T("Fill Color is: %d; %d; %d"),
    GetRValue(m_animationColor),
    GetGValue(m_animationColor),
    GetBValue(m_animationColor));

 
    dc.DrawText(strRGB,
    rect,
    DT_CENTER);

    rect.top += nInfoAreaHeight;  
 
    CBrush br;  
 
    br.CreateSolidBrush(m_animationColor);

 CBrush* pBrushOld = dc.SelectObject(&br);

 
    dc.Rectangle((CRect)m_animationRect);

 dc.SelectObject(pBrushOld);

 }  
 ```  
  
9. Al final del archivo, agregue el código siguiente.  
  
 ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
 {  
    static UI_ANIMATION_SECONDS duration = 3;  
    static DOUBLE dblSpeed = 35.;  
    static BYTE nStartColor = 50;  
    static BYTE nEndColor = 255;  
 
    BYTE nRedColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nGreenColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nBlueColorFinal = bDirection  nStartColor : nEndColor;  
 
    CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

    CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

    CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

 
    m_animationColor.AddTransition(pRedTransition,
    pGreenTransition,
    pBlueTransition);

 
    CRect rectClient;  
    GetClientRect(rectClient);

 rectClient.top += nInfoAreaHeight;  
 
    int nLeftFinal = bDirection  rectClient.left : rectClient.CenterPoint().x;  
    int nTopFinal = bDirection  rectClient.top : rectClient.CenterPoint().y;  
    int nRightFinal = bDirection  rectClient.right : rectClient.CenterPoint().x;  
    int nBottomFinal = bDirection  rectClient.bottom : rectClient.CenterPoint().y;  
 
    CLinearTransition* pLeftTransition = new CLinearTransition(duration,
    nLeftFinal);

    CLinearTransition* pTopTransition = new CLinearTransition(duration,
    nTopFinal);

    CLinearTransition* pRightTransition = new CLinearTransition(duration,
    nRightFinal);

    CLinearTransition* pBottomTransition = new CLinearTransition(duration,
    nBottomFinal);

 
    m_animationRect.AddTransition(pLeftTransition,
    pTopTransition,
    pRightTransition,
    pBottomTransition);

 
    CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();
CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup,
    pBlueTransition);

 
    pLeftTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pTopTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pRightTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pBottomTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

 
    m_animationController.AnimateGroup(nAnimationGroup);

 }  
 ```  
  
10. En el **proyecto** menú, haga clic en **Asistente para clases**.  
  
11. En el **Asistente para clases MFC**, en **nombre de la clase**, seleccione `CMFCAnimationWalkthroughView`.  
  
12. En el **mensajes** ficha la **mensajes** cuadro, seleccione `WM_ERASEBKGND`, haga clic en **Agregar controlador**y, a continuación, haga clic en **Aceptar**.  
  
13. En MFCAnimationWalkthroughView.cpp, reemplace la implementación de `OnEraseBkgnd` con el código siguiente para reducir el parpadeo en el objeto animado cuando se vuelve a dibujarse.  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
 {  
    return TRUE;  
 }  
 ```  
  
14. Reemplace las implementaciones de `CMFCAnimationWalkthroughView::OnAnimationStartforward`, `CMFCAnimationWalkthroughView::OnAnimationStartbackward`, y `CMFCAnimationWalkthroughView::OnAnimationStop` con el código siguiente.  
  
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
  
### <a name="to-center-the-animated-object-in-the-window"></a>Para centrar el objeto animado en la ventana  
  
1.  En **el Explorador de soluciones**, haga doble clic en MFCAnimationWalkthroughView.h para abrirlo para modificarlo. Al final de la `CMFCAnimationWalkthroughView` (clase), justo después de la definición de `m_animationRect`, agregue el código siguiente.  
  
 ```  
    BOOL m_bCurrentDirection;  
 ```  
  
2.  Guarde el archivo y ciérrelo.  
  
3.  En el **proyecto** menú, haga clic en **Asistente para clases**.  
  
4.  En el **Asistente para clases MFC**, en **nombre de la clase**, seleccione `CMFCAnimationWalkthroughView`.  
  
5.  En el **mensajes** ficha la **mensajes** cuadro, seleccione `WM_SIZE`, haga clic en **Agregar controlador**y, a continuación, haga clic en **Aceptar**.  
  
6.  En MFCAnimationWalkthroughView.cpp, reemplace el código para `CMFCAnimationWalkthroughView::OnSize` con el código siguiente.  
  
 ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

 
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
  
7.  Al principio del constructor para `CMFCAnimationWalkthroughView`, agregue el código siguiente.  
  
 ```  
    m_bCurrentDirection = TRUE;  
 ```  
  
8.  Al principio de la `CMFCAnimationWalkthroughView::Animate` método, agregue el código siguiente.  
  
 ```  
    m_bCurrentDirection = bDirection;  
 ```  
  
9. Guarde el archivo y ciérrelo.  
  
### <a name="to-verify-the-results"></a>Para comprobar los resultados  
  
1.  Compile y ejecute la aplicación. En el **animación** menú, haga clic en **iniciar al día**. Un rectángulo debe aparecer y, a continuación, rellenar el área central. Al hacer clic en **iniciar con versiones anteriores**debe invertir la animación y, al hacer clic en **detener**, se detiene. Debe cambiar el color de relleno del rectángulo de medida que avanza la animación y el color actual se debe mostrar en la parte superior de la ventana de la animación.  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales](../mfc/walkthroughs-mfc.md)

