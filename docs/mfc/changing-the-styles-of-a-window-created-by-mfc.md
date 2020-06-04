---
title: Cambiar los estilos de una ventana creada por MFC
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374591"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Cambiar los estilos de una ventana creada por MFC

En su versión de la `WinMain` función, MFC registra varias clases de ventana estándar automáticamente. Dado que normalmente no edita `WinMain`MFC, esa función no ofrece ninguna oportunidad de cambiar los estilos de ventana predeterminados de MFC. En este artículo se explica cómo puede cambiar los estilos de una clase de ventana preregistrada en una aplicación existente.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Cambio de estilos en una nueva aplicación MFC

Si usa Visual C++ 2.0 o posterior, puede cambiar los estilos de ventana predeterminados en el Asistente para aplicaciones al crear la aplicación. En la página Características de la interfaz de usuario del Asistente para aplicaciones, puede cambiar los estilos de la ventana de marco principal y las ventanas secundarias MDI. Para cualquier tipo de ventana, puede especificar su grosor de marco (grueso o delgado) y cualquiera de los siguientes:

- Si la ventana tiene controles Minimizar o Maximizar.

- Si la ventana aparece inicialmente minimizada, maximizada o ninguna.

Para las ventanas de marco principal, también puede especificar si la ventana tiene un menú del sistema. Para las ventanas secundarias MDI, puede especificar si la ventana admite paneles divisores.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Cambio de estilos en una aplicación existente

Si va a cambiar los atributos de ventana en una aplicación existente, siga las instrucciones del resto de este artículo en su lugar.

Para cambiar los atributos de ventana predeterminados utilizados por una aplicación de marco de trabajo creada con el Asistente para aplicaciones, reemplace la función miembro virtual [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) de la ventana. `PreCreateWindow`permite que una aplicación acceda al proceso de creación normalmente administrado internamente por la [Clase CDocTemplate.](../mfc/reference/cdoctemplate-class.md) El marco `PreCreateWindow` de trabajo llama justo antes de crear la ventana. Al modificar la estructura `PreCreateWindow` [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) pasada a , la aplicación puede cambiar los atributos utilizados para crear la ventana. Por ejemplo, para asegurarse de que una ventana no utiliza un título, utilice la siguiente operación bit a bit:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

La aplicación de ejemplo [CTRLBARS](../overview/visual-cpp-samples.md) muestra esta técnica para cambiar los atributos de ventana. Dependiendo de lo que `PreCreateWindow`cambie la aplicación, puede ser necesario llamar a la implementación de la clase base de la función.

La siguiente discusión abarca el caso SDI y el [caso MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>El caso SDI

En una sola aplicación de interfaz de documento (SDI), el estilo de ventana predeterminado en el marco de trabajo es una combinación de los **estilos WS_OVERLAPPEDWINDOW** y **FWS_ADDTOTITLE.** **FWS_ADDTOTITLE** es un estilo específico de MFC que indica al marco de trabajo que agregue el título del documento al título de la ventana. Para cambiar los atributos de ventana `PreCreateWindow` en una aplicación SDI, reemplace la función de la clase derivada (de `CFrameWnd` la que el Asistente para aplicaciones nombra `CMainFrame`). Por ejemplo:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Este código crea una ventana de marco principal sin botones Minimizar y Maximizar y sin un borde considerable. La ventana se centra inicialmente en la pantalla.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>El caso MDI

Se requiere un poco más de trabajo para cambiar el estilo de ventana de una ventana secundaria en una aplicación de interfaz de varios documentos (MDI). De forma predeterminada, una aplicación MDI creada con el Asistente para aplicaciones utiliza la clase [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) predeterminada definida en MFC. Para cambiar el estilo de ventana de una ventana secundaria `CMDIChildWnd` MDI, `CMDIChildWnd` debe derivar una nueva clase y reemplazar todas las referencias al proyecto con referencias a la nueva clase. Lo más probable es `CMDIChildWnd` que la única referencia en `InitInstance` la aplicación se encuentra en la función miembro de la aplicación.

El estilo de ventana predeterminado utilizado en una aplicación MDI es una combinación de los estilos **WS_CHILD**, **WS_OVERLAPPEDWINDOW**y **FWS_ADDTOTITLE.** Para cambiar los atributos de ventana de las ventanas secundarias de una `CMDIChildWnd`aplicación MDI, reemplace la función [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) de la clase derivada de . Por ejemplo:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Este código crea ventanas secundarias MDI sin un botón Maximizar.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Estilos de Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)

- [Estilos de ventana](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Consulte también

[Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)
