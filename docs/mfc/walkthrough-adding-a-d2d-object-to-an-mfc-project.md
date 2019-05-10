---
title: 'Tutorial: Agregar objetos D2D a un proyecto MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5710add59c0e5d27b2969ae22087533cae901ca9
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558177"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Tutorial: Agregar objetos D2D a un proyecto MFC

En este tutorial se enseña cómo agregar un Direct2D básica (D2D) a objeto Visual C++, el proyecto de biblioteca de clases (MFC) de Microsoft Foundation y, a continuación, compile el proyecto en una aplicación que imprime "Hello, world" en un fondo degradado.

El tutorial muestra cómo realizar estas tareas:

- Crear una aplicación MFC.

- Crear un pincel de color sólido y un pincel de degradado lineal.

- Modifique el pincel de degradado para que el cambio se realizará correctamente cuando se cambia el tamaño de la ventana.

- Implemente un controlador de dibujo D2D.

- Compruebe los resultados.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Requisitos previos

Para completar este tutorial, debe tener instalado Visual Studio con el **desarrollo de escritorio con C++** carga de trabajo y la propiedad opcional **MFC de Visual C++ para x86 y x64** componente.

## <a name="to-create-an-mfc-application"></a>Para crear una aplicación MFC

1. Use la **MFC Application Wizard** para crear una aplicación MFC. Vea [Tutorial: Usar los nuevos controles de Shell de MFC](walkthrough-using-the-new-mfc-shell-controls.md) para obtener instrucciones sobre cómo abrir el Asistente para la versión de Visual Studio.

1. En el **nombre** , escriba *MFCD2DWalkthrough*. Elija **Aceptar**.

1. En el **MFC Application Wizard**, elija **finalizar** sin cambiar la configuración.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Para crear un pincel de color sólido y un pincel de degradado lineal

1. En **el Explorador de soluciones**, en el **MFCD2DWalkthrough** del proyecto, en el **archivos de encabezado** carpeta, abra MFCD2DWalkthroughView.h. Agregue este código a la `CMFCD2DWalkthroughView` clase para crear tres variables de datos:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Guarde el archivo y ciérrelo.

1. En el **archivos de código fuente** carpeta, abra MFCD2DWalkthroughView.cpp. En el constructor para la `CMFCD2DWalkthroughView` de clases, agregue este código:

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

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Para modificar el pincel de degradado para que el cambio se realizará correctamente cuando se cambia el tamaño de la ventana

1. En el **proyecto** menú, elija **Class Wizard**.

1. En el **Asistente para clases MFC**, en **nombre de la clase**, seleccione `CMFCD2DWalkthroughView`.

1. En el **mensajes** ficha la **mensajes** cuadro, seleccione `WM_SIZE` y, a continuación, elija **Agregar controlador**. Esta acción agrega el `OnSize` controlador de mensajes para el `CMFCD2DWalkthroughView` clase.

1. En el **los controladores existentes** cuadro, seleccione `OnSize`. Elija **modificar código** para mostrar el `CMFCD2DWalkthroughView::OnSize` método. Al final del método, agregue el código siguiente.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Guarde el archivo y ciérrelo.

## <a name="to-implement-a-d2d-drawing-handler"></a>Para implementar un controlador de dibujo D2D

1. En el **proyecto** menú, elija **Class Wizard**.

1. En el **Asistente para clases MFC**, en **nombre de la clase**, seleccione `CMFCD2DWalkthroughView`.

1. En el **mensajes** ficha, elija **Agregar mensaje personalizado**.

1. En el **Agregar mensaje personalizado** cuadro de diálogo el **mensaje de Windows personalizada** , escriba *AFX_WM_DRAW2D*. En el **nombre de controlador de mensaje** , escriba *OnDraw2D*. Seleccione el **mensaje registrado** opción y, a continuación, elija **Aceptar**. Esta acción agrega un controlador de mensajes para que el mensaje AFX_WM_DRAW2D el `CMFCD2DWalkthroughView` clase.

1. En el **los controladores existentes** cuadro, seleccione `OnDraw2D`. Elija **modificar código** para mostrar el `CMFCD2DWalkthroughView::OnDraw2D` método. Use este código para el `CMFCD2DWalkthroughView::OnDrawD2D` método:

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

Compile y ejecute la aplicación. Debe tener un rectángulo degradado que cambia cuando cambia el tamaño de la ventana. "¡Hello World!" se debe mostrar en el centro del rectángulo.

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)
