---
title: 'Tutorial: Agregar objetos D2D a un proyecto de MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5e1c75e32899ef9697025d662eeec4a6a2482f2b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304295"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Tutorial: Agregar objetos D2D a un proyecto de MFC

En este tutorial se enseña cómo agregar un objeto de Direct2D básico (D2D) a C++un proyecto Visual, biblioteca MFC (MFC) y, a continuación, compilar el proyecto en una aplicación que imprime "Hello, World!" en un fondo degradado.

En el tutorial se muestra cómo realizar estas tareas:

- Cree una aplicación MFC.

- Cree un pincel de color sólido y un pincel de degradado lineal.

- Modifique el pincel de degradado para que cambie correctamente cuando se cambie el tamaño de la ventana.

- Implemente un controlador de dibujo de D2D.

- Compruebe los resultados.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe tener Visual Studio instalado con el **desarrollo de escritorio con C++**  carga de trabajo y el componente opcional **Visual C++ MFC para x86 y x64** .

## <a name="to-create-an-mfc-application"></a>Para crear una aplicación MFC

1. Utilice el **Asistente para aplicaciones MFC** para crear una aplicación MFC. Vea [Tutorial: usar los nuevos controles de Shell de MFC](walkthrough-using-the-new-mfc-shell-controls.md) para obtener instrucciones sobre cómo abrir el Asistente para su versión de Visual Studio.

1. En el cuadro **nombre** , escriba *MFCD2DWalkthrough*. Elija **Aceptar**.

1. En el **Asistente para aplicaciones MFC**, elija **Finalizar** sin cambiar la configuración.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Para crear un pincel de color sólido y un pincel de degradado lineal

1. En **Explorador de soluciones**, en el proyecto **MFCD2DWalkthrough** , en la carpeta **header files** , abra MFCD2DWalkthroughView. h. Agregue este código a la clase `CMFCD2DWalkthroughView` para crear tres variables de datos:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Guarde el archivo y ciérrelo.

1. En la carpeta **archivos de código fuente** , abra MFCD2DWalkthroughView. cpp. En el constructor de la clase `CMFCD2DWalkthroughView`, agregue este código:

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   Guarde el archivo y ciérrelo.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Para modificar el pincel de degradado de modo que cambie correctamente cuando se cambie el tamaño de la ventana

1. En el menú **proyecto** , elija **Asistente para clases**.

1. En el **Asistente para clases MFC**, en **nombre de clase**, seleccione `CMFCD2DWalkthroughView`.

1. En la pestaña **mensajes** , en el cuadro **mensajes** , seleccione `WM_SIZE` y, a continuación, elija **Agregar controlador**. Esta acción agrega el controlador de mensajes `OnSize` a la clase `CMFCD2DWalkthroughView`.

1. En el cuadro **controladores existentes** , seleccione `OnSize`. Elija **editar código** para mostrar el método `CMFCD2DWalkthroughView::OnSize`. Al final del método, agregue el código siguiente.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Guarde el archivo y ciérrelo.

## <a name="to-implement-a-d2d-drawing-handler"></a>Para implementar un controlador de dibujo de D2D

1. En el menú **proyecto** , elija **Asistente para clases**.

1. En el **Asistente para clases MFC**, en **nombre de clase**, seleccione `CMFCD2DWalkthroughView`.

1. En la pestaña **mensajes** , elija **Agregar mensaje personalizado**.

1. En el cuadro de diálogo **Agregar mensaje personalizado** , en el cuadro de **mensaje de Windows personalizado** , escriba *AFX_WM_DRAW2D*. En el cuadro **nombre del controlador de mensajes** , escriba *OnDraw2D*. Seleccione la opción **mensaje registrado** y, a continuación, elija **Aceptar**. Esta acción agrega un controlador de mensajes para el mensaje AFX_WM_DRAW2D a la clase `CMFCD2DWalkthroughView`.

1. En el cuadro **controladores existentes** , seleccione `OnDraw2D`. Elija **editar código** para mostrar el método `CMFCD2DWalkthroughView::OnDraw2D`. Use este código para el método `CMFCD2DWalkthroughView::OnDrawD2D`:

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   Guarde el archivo y ciérrelo.

## <a name="to-verify-the-results"></a>Para comprobar los resultados

Compile y ejecute la aplicación. Debe tener un rectángulo de degradado que cambie al cambiar el tamaño de la ventana. "Hello World!" debe mostrarse en el centro del rectángulo.

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)
