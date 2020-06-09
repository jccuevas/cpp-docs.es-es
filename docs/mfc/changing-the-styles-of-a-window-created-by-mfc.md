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
ms.openlocfilehash: f3fd9f83112737e944d83cf00da685d81fe8b2a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624948"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Cambiar los estilos de una ventana creada por MFC

En su versión de la `WinMain` función, MFC registra varias clases de ventana estándar. Dado que normalmente no se editan `WinMain` las MFC, esta función no tiene la oportunidad de cambiar los estilos de ventana predeterminados de MFC. En este artículo se explica cómo puede cambiar los estilos de una clase de ventana previamente registrada en una aplicación existente.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Cambiar estilos en una nueva aplicación MFC

Si utiliza Visual C++ 2,0 o posterior, puede cambiar los estilos de ventana predeterminados en el Asistente para aplicaciones cuando cree la aplicación. En la página características de la interfaz de usuario del Asistente para aplicaciones, puede cambiar los estilos de la ventana de marco principal y las ventanas secundarias MDI. Para cualquier tipo de ventana, puede especificar el grosor del marco (grueso o fino) y cualquiera de los siguientes:

- Indica si la ventana tiene los controles minimizar o maximizar.

- Indica si la ventana aparece inicialmente minimizada, maximizada o ninguna de ellas.

En el caso de las ventanas de marco principal, también puede especificar si la ventana tiene un menú del sistema. En el caso de las ventanas secundarias MDI, puede especificar si la ventana admite paneles divisores.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Cambiar estilos en una aplicación existente

Si va a cambiar los atributos de ventana en una aplicación existente, siga las instrucciones del resto de este artículo en su lugar.

Para cambiar los atributos de ventana predeterminados usados por una aplicación de marco creada con el Asistente para aplicaciones, invalide la función miembro virtual [PreCreateWindow](reference/cwnd-class.md#precreatewindow) de la ventana. `PreCreateWindow`permite a una aplicación tener acceso al proceso de creación que normalmente administra internamente la clase [CDocTemplate](reference/cdoctemplate-class.md) . El marco de trabajo llama `PreCreateWindow` justo antes de crear la ventana. Al modificar la estructura [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) pasada a `PreCreateWindow` , la aplicación puede cambiar los atributos utilizados para crear la ventana. Por ejemplo, para asegurarse de que una ventana no usa un título, use la siguiente operación bit a bit:

[!code-cpp[NVC_MFCDocView#15](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

La aplicación de ejemplo [CTRLBARS](../overview/visual-cpp-samples.md) demuestra esta técnica para cambiar los atributos de la ventana. En función de lo que cambie la aplicación `PreCreateWindow` , puede que sea necesario llamar a la implementación de la clase base de la función.

En el siguiente debate se tratan los casos SDI y [MDI](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>El caso SDI

En una aplicación de interfaz de un único documento (SDI), el estilo de ventana predeterminado en el marco es una combinación de los estilos **WS_OVERLAPPEDWINDOW** y **FWS_ADDTOTITLE** . **FWS_ADDTOTITLE** es un estilo específico de MFC que indica al marco de trabajo que agregue el título del documento al título de la ventana. Para cambiar los atributos de ventana en una aplicación SDI, invalide la `PreCreateWindow` función en la clase derivada de `CFrameWnd` (que es el nombre del Asistente para aplicaciones `CMainFrame` ). Por ejemplo:

[!code-cpp[NVC_MFCDocViewSDI#11](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Este código crea una ventana de marco principal sin los botones minimizar y maximizar y sin un borde ajustable. La ventana se centra inicialmente en la pantalla.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>El caso de MDI

Se requiere un poco más de trabajo para cambiar el estilo de ventana de una ventana secundaria en una aplicación de interfaz de múltiples documentos (MDI). De forma predeterminada, una aplicación MDI creada con el Asistente para aplicaciones utiliza la clase [CMDIChildWnd](reference/cmdichildwnd-class.md) predeterminada definida en MFC. Para cambiar el estilo de ventana de una ventana secundaria MDI, debe derivar una nueva clase de `CMDIChildWnd` y reemplazar todas las referencias a `CMDIChildWnd` en el proyecto con referencias a la nueva clase. Lo más probable es que la única referencia a `CMDIChildWnd` en la aplicación se encuentre en la `InitInstance` función miembro de la aplicación.

El estilo de ventana predeterminado utilizado en una aplicación MDI es una combinación de los estilos **WS_CHILD**, **WS_OVERLAPPEDWINDOW**y **FWS_ADDTOTITLE** . Para cambiar los atributos de ventana de las ventanas secundarias de una aplicación MDI, invalide la función [PreCreateWindow](reference/cwnd-class.md#precreatewindow) en la clase derivada de `CMDIChildWnd` . Por ejemplo:

[!code-cpp[NVC_MFCDocView#16](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Este código crea ventanas secundarias MDI sin un botón maximizar.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Estilos de Windows](reference/styles-used-by-mfc.md#window-styles)

- [Estilos de ventana de marco](frame-window-styles-cpp.md)

- [Estilos de ventana](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Consulte también

[Estilos de ventana de marco](frame-window-styles-cpp.md)
