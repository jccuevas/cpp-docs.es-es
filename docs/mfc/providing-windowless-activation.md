---
title: "Proporcionar activación sin ventana | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb33f1dd9f8be8cb06cdfcc2aeecb653c2762410
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="providing-windowless-activation"></a>Proporcionar activación sin ventana
Código de creación de ventana (es decir, todo lo que ocurre cuando se llama a **CreateWindow**) es costoso para ejecutar. Un control que mantiene una pantalla ventana tiene que administrar los mensajes de la ventana. Controles sin ventana, por tanto, son más rápidos que los controles de windows.  
  
 Una ventaja adicional de los controles sin ventana es que, a diferencia de los controles con ventanas, controles sin ventana admiten pintura transparente y regiones de pantalla no rectangular. Un ejemplo común de un control transparente es un control de texto con un fondo transparente. Los controles se dibuja el texto pero no en el fondo, para que lo que está bajo el texto se muestra a través de. Formularios más reciente a menudo hacen que el uso de los controles no rectangulares, como flechas y botones de ida y vuelta.  
  
 A menudo, un control no es necesario que una ventana de su propio y, en su lugar, puede usar los servicios de Windows de su contenedor, siempre que el contenedor se ha escrito para admitir los objetos sin ventana. Controles sin ventana son compatibles con contenedores más antiguos. En contenedores antiguos no diseñados para admitir controles sin ventana, los controles sin ventana crean una ventana cuando está activo.  
  
 Dado que los controles sin ventana no tienen sus propias ventanas, el contenedor (que tienen una ventana) es responsable de proporcionar servicios que en caso contrario, habría sido proporcionados por la ventana del control. Por ejemplo, si el control necesita consultar el foco del teclado, capturar el mouse o para obtener un contexto de dispositivo, estas operaciones se administran por el contenedor. El contenedor enruta los mensajes de entrada del usuario se envía a su ventana para el control sin ventana apropiado, mediante la `IOleInPlaceObjectWindowless` interfaz. (Consulte la *ActiveX SDK* para obtener una descripción de esta interfaz.) `COleControl` estos servicios desde el contenedor de invocación de funciones miembro.  
  
 Para hacer que el control utilice activación sin ventana, incluya el **windowlessActivate** marca en el conjunto de indicadores devuelto por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]  
  
 El código para incluir este indicador se genera automáticamente si selecciona la **activación sin ventana** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página del Asistente para el Control de ActiveX de MFC.  
  
 Cuando se habilita la activación sin ventana, el contenedor delegará los mensajes de entrada para el control `IOleInPlaceObjectWindowless` interfaz. `COleControl`de la implementación de esta interfaz envía los mensajes a través de mapas de mensajes del control, después de ajustar el mouse coordina adecuadamente. Puede procesar los mensajes como mensajes de ventana normal, agregando las entradas correspondientes al mapa de mensajes. En los controladores para estos mensajes, evite utilizar el `m_hWnd` variable miembro (o cualquier función miembro que lo utilice) sin comprobar primero que su valor no es **NULL**.  
  
 `COleControl`proporciona funciones miembro que invocan la captura del mouse, foco del teclado, desplazamiento y otros servicios de ventana del contenedor según corresponda, incluidas:  
  
-   [GetFocus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)  
  
-   [GetCapture](../mfc/reference/colecontrol-class.md#getcapture), [SetCapture](../mfc/reference/colecontrol-class.md#setcapture), [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)  
  
-   [GetDC](../mfc/reference/colecontrol-class.md#getdc), [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)  
  
-   [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)  
  
-   [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)  
  
-   [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)  
  
 En los controles sin ventana, debe utilizar siempre el `COleControl` funciones de miembro en lugar de los correspondientes `CWnd` las funciones miembro o sus funciones relacionadas de la API de Win32.  
  
 Puede que desee un control sin ventana sea el destino de una operación de arrastrar y colocar OLE. Normalmente, esto requeriría que la ventana del control registrarse como un destino de colocación. Puesto que el control no tiene ninguna ventana propia, el contenedor utiliza su propia ventana como un destino de colocación. El control proporciona una implementación de la `IDropTarget` interfaz a la que el contenedor puede delegar llamadas en el momento adecuado. Para exponer esta interfaz al contenedor, invalidar [COleControl:: GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

