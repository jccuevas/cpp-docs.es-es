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
ms.openlocfilehash: 0a002badf9c20ca7b2d1a129eca069e586893f3c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767241"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Cambiar los estilos de una ventana creada por MFC

En su versión de la `WinMain` función, MFC registra varias clases de ventana estándar para usted. Dado que normalmente no editar de MFC `WinMain`, que función no permite cambiar los estilos de ventana predeterminados MFC. En este artículo se explica cómo puede cambiar los estilos de esta clase de ventana registrada previamente en una aplicación existente.

##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> Cambiar estilos en una nueva aplicación MFC

Si usa Visual C++ 2.0 o posterior, puede cambiar los estilos de ventana predeterminado en el Asistente para la aplicación cuando se crea la aplicación. En la página de características de la interfaz de usuario del Asistente de aplicación, puede cambiar los estilos para la ventana de marco principal y las ventanas secundarias MDI. Para cualquier tipo de ventana, puede especificar su grosor del marco (grueso o fino) y ninguno de los siguientes:

- Determina si la ventana tiene controles minimizar o maximizar.

- Si la ventana aparece inicialmente minimizada, maximizada, o ninguno.

Para las ventanas de marco principal, también puede especificar si la ventana tiene un menú de sistema. Ventanas secundarias MDI, puede especificar si la ventana admite paneles del divisor.

##  <a name="_core_changing_styles_in_an_existing_application"></a> Cambiar estilos en una aplicación existente

Si va a cambiar atributos de ventana en una aplicación existente, siga las instrucciones en el resto de este artículo en su lugar.

Para cambiar los atributos de ventana predeterminado utilizados por una aplicación de marco de trabajo creada con el Asistente para aplicaciones, reemplace la ventana [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) función miembro virtual. `PreCreateWindow` permite que una aplicación tenga acceso el proceso de creación normalmente se administra internamente por la [CDocTemplate](../mfc/reference/cdoctemplate-class.md) clase. Las llamadas de framework `PreCreateWindow` justo antes de crear la ventana. Modificando el [CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) estructura pasada a `PreCreateWindow`, la aplicación puede modificar los atributos utilizados para crear la ventana. Por ejemplo, para asegurarse de que una ventana no utiliza un título, utilice la siguiente operación bit a bit:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

El [CTRLBARS](../overview/visual-cpp-samples.md) aplicación de ejemplo demuestra esta técnica para cambiar los atributos de la ventana. Dependiendo de lo que la aplicación cambia en `PreCreateWindow`, puede ser necesario llamar a la implementación de la función de la clase base.

En la siguiente explicación se trata el caso de SDI y [caso MDI](#_core_the_mdi_case).

##  <a name="_core_the_sdi_case"></a> El caso de SDI

En una aplicación de único documento (SDI) de la interfaz, el estilo de ventana predeterminado en el marco de trabajo es una combinación de la **WS_OVERLAPPEDWINDOW** y **FWS_ADDTOTITLE** estilos. **FWS_ADDTOTITLE** es un estilo específico de MFC que indica el marco de trabajo para agregar el título del documento para el título de la ventana. Para cambiar los atributos de ventana en una aplicación SDI, reemplace el `PreCreateWindow` función en la clase derivada de `CFrameWnd` (que los nombres del Asistente para aplicaciones `CMainFrame`). Por ejemplo:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Este código crea una ventana de marco principal sin botones Minimizar y maximizar y sin un borde de tamaño ajustable. Inicialmente, la ventana se centra en la pantalla.

##  <a name="_core_the_mdi_case"></a> El caso MDI

Se requiere un poco más trabajo para cambiar el estilo de ventana de una ventana secundaria en una aplicación de múltiples documentos (MDI) de la interfaz. De forma predeterminada, una aplicación MDI creada con el Asistente para la aplicación usa el valor predeterminado [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) clase definida en MFC. Para cambiar el estilo de ventana de una ventana secundaria MDI, debe derivar una nueva clase de `CMDIChildWnd` y reemplace todas las referencias a `CMDIChildWnd` en el proyecto con referencias a la nueva clase. Probablemente, la única referencia a `CMDIChildWnd` en la aplicación se encuentra en la aplicación `InitInstance` función miembro.

El estilo de ventana predeterminado utilizado en una aplicación MDI es una combinación de la **WS_CHILD**, **WS_OVERLAPPEDWINDOW**, y **FWS_ADDTOTITLE** estilos. Para cambiar los atributos de la ventana de las ventanas secundarias de una aplicación MDI, reemplace el [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) función en la clase derivada de `CMDIChildWnd`. Por ejemplo:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Este código crea el formulario secundario MDI windows sin un botón Maximizar.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Estilos de Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)

- [Estilos de ventana](/windows/desktop/winmsg/window-styles)

## <a name="see-also"></a>Vea también

[Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)
