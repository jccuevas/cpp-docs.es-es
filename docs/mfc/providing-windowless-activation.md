---
title: Proporcionar activación sin ventana
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: 9d60c309d5644c106e6c85a0c7b3988916be7193
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284715"
---
# <a name="providing-windowless-activation"></a>Proporcionar activación sin ventana

Código de creación de ventana (es decir, todo lo que ocurre cuando se llama a `CreateWindow`) es el costo de ejecutar. Un control que mantiene una pantalla ventana tiene que administrar los mensajes de la ventana. Los controles sin ventana, por tanto, son más rápidos que los controles de windows.

Una ventaja adicional de los controles sin ventana es que, a diferencia de los controles con ventanas, los controles sin ventana admiten dibujo transparente y regiones de pantalla no rectangulares. Un ejemplo común de un control transparente es un control de texto con un fondo transparente. Los controles se pinta el texto, pero no en segundo plano, por lo que cualquier cosa que esté bajo el texto se muestra a través. A menudo, los formularios más reciente que el uso de controles no rectangulares, como flechas y botones redondos.

A menudo, un control no es necesario que una ventana de su propia y, en su lugar, puede usar los servicios de Windows de su contenedor, siempre que el contenedor se ha escrito para admitir los objetos sin ventana. Los controles sin ventana son compatibles con contenedores más antiguos. En contenedores antiguos no diseñados para admitir controles sin ventanas, los controles sin ventana crean una ventana cuando está activo.

Dado que los controles sin ventana no tienen sus propias ventanas, el contenedor (que tienen una ventana) es responsable de proporcionar servicios que en caso contrario, se habría proporcionados por la ventana del control. Por ejemplo, si el control necesita consultar el foco del teclado, capturar el mouse u obtener un contexto de dispositivo, estas operaciones son administradas por el contenedor. El contenedor enruta los mensajes de entrada del usuario se envía a su ventana para el control sin ventanas adecuado, utilizando el `IOleInPlaceObjectWindowless` interfaz. (Consulte la *ActiveX SDK* para obtener una descripción de esta interfaz.) `COleControl` funciones miembro invocan estos servicios desde el contenedor.

Para hacer que el control utilice activación sin ventana, incluya el **windowlessActivate** marca en el conjunto de indicadores devueltos por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

El código para incluir esta marca se genera automáticamente si selecciona la **activación sin ventana** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página del Asistente para el Control de ActiveX de MFC.

Cuando se habilita la activación sin ventana, el contenedor delegará mensajes de entrada para el control `IOleInPlaceObjectWindowless` interfaz. `COleControl`de implementación de esta interfaz envía los mensajes a través de mapas de mensajes de control, después de ajustar el mouse coordina adecuadamente. Puede procesar los mensajes como mensajes de ventana normal, agregando las entradas correspondientes en el mapa de mensajes. En los controladores para estos mensajes, evite usar el *m_hWnd* variable miembro (o cualquier función miembro que lo utiliza) sin antes comprobar que su valor no es **NULL**.

`COleControl` proporciona funciones miembro que invocan la captura del mouse, foco de teclado, desplazamiento y otros servicios de la ventana del contenedor según corresponda, incluyendo:

- [GetFocus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

En los controles sin ventana, debe usar siempre el `COleControl` funciones miembro en lugar de la correspondiente `CWnd` funciones miembro o sus funciones relacionadas de la API de Win32.

Puede ser el destino de una operación de arrastrar y colocar OLE de un control sin ventanas. Normalmente, esto requeriría que la ventana del control se ha registrado como un destino de colocación. Puesto que el control no tiene ninguna ventana propia, el contenedor usa su propia ventana como un destino de colocación. El control proporciona una implementación de la `IDropTarget` interfaz a la que el contenedor puede delegar las llamadas en el momento adecuado. Para exponer esta interfaz para el contenedor, invalidar [COleControl:: GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Por ejemplo:

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)
