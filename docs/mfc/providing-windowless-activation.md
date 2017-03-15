---
title: "Proporcionar activaci&#243;n sin ventana | Microsoft Docs"
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
  - "activación [C++], controles ActiveX en MFC"
  - "activación [C++], sin ventana"
  - "controles ActiveX en MFC [C++], opciones para activar"
  - "activación sin ventana de los controles ActiveX en MFC"
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Proporcionar activaci&#243;n sin ventana
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El código de creación de la ventana \(es decir, todo lo que sucede cuando se llama a **CreateWindow**\) es costosa.  Un control que mantiene una ventana en pantalla tiene que controlar los mensajes de la ventana.  Los controles sin ventana son por consiguiente más rápidamente que los controles con las ventanas.  
  
 Otra ventaja de controles sin ventana es que, a diferencia de los controles con, los controles sin ventana admiten el dibujo transparente y zonas de la pantalla rectangular.  Un ejemplo común de un control transparente es un control de texto con un fondo transparente.  Los controles pintan texto pero no el fondo, lo que lo que haya bajo el texto muestra a través de.  Más nuevos formularios utilizan a menudo de controles rectangular, como flechas y botones redondos.  
  
 A menudo, un control no necesita una ventana propio y, en su lugar, no puede utilizar los servicios de la ventana de su contenedor, siempre que el contenedor se ha escrito para admitir objetos sin ventana.  Los controles sin ventana son compatibles con contenedores más antiguos.  En contenedores más antiguos no escritos para admitir los controles sin ventana, los controles sin ventana crean una ventana cuando está activo.  
  
 Dado que los controles sin ventana no tienen sus propias ventanas, el contenedor \(que tiene una ventana\) es responsable de proporcionar los servicios que pudieran estar proporcionados de otra manera por la propia ventana de control.  Por ejemplo, si el control necesita consultar el foco de teclado, capturar el mouse, u obtener un contexto de dispositivo, estas operaciones son administradas por el contenedor.  El contenedor enruta los mensajes de datos proporcionados por el usuario enviados a la ventana al control sin ventana adecuado, mediante la interfaz de `IOleInPlaceObjectWindowless` . \(Vea *ActiveX SDK* para obtener una descripción de esta interfaz.\) las funciones miembro de `COleControl` invocar estos servicios del contenedor.  
  
 Para crear el uso del control activación sin ventana, incluya la marca de **windowlessActivate** en el conjunto de indicadores devueltos por [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md).  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/CPP/providing-windowless-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/CPP/providing-windowless-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/CPP/providing-windowless-activation_3.cpp)]  
  
 El código para incluir este marcador se genera automáticamente si selecciona la opción de **Windowless activation** en la página de [Configuración del control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) del asistente para controles ActiveX MFC.  
  
 Cuando se habilita la activación sin ventana, el contenedor delegará mensajes de entrada a la interfaz de `IOleInPlaceObjectWindowless` del control.  la implementación de`COleControl` de esta interfaz envía los mensajes a través del mapa de mensajes del control, después de ajustar las coordenadas del mouse correctamente.  Puede procesar los mensajes como mensajes normales de la ventana, agregando las entradas correspondientes al mapa de mensajes.  En los controladores para estos mensajes, evite utilizar la variable miembro de `m_hWnd` \(o cualquier función miembro que lo utilice\) sin comprobar primero que su valor no es **nulo**.  
  
 `COleControl` proporciona funciones miembro que invocan captura del mouse, el foco de teclado, el desplazamiento, y otros servicios de la ventana contenedora como adecuado, como:  
  
-   [GetFocus](../Topic/COleControl::GetFocus.md), [SetFocus](../Topic/COleControl::SetFocus.md)  
  
-   [GetCapture](../Topic/COleControl::GetCapture.md), [SetCapture](../Topic/COleControl::SetCapture.md), [ReleaseCapture](../Topic/COleControl::ReleaseCapture.md)  
  
-   [GetDC](../Topic/COleControl::GetDC.md), [ReleaseDC](../Topic/COleControl::ReleaseDC.md)  
  
-   [InvalidateRgn](../Topic/COleControl::InvalidateRgn.md)  
  
-   [ScrollWindow](../Topic/COleControl::ScrollWindow.md)  
  
-   [GetClientRect](../Topic/COleControl::GetClientRect.md)  
  
 En controles sin ventana, debe utilizar siempre las funciones miembro de `COleControl` en lugar de las funciones correspondientes del miembro de `CWnd` o de sus funciones relacionadas de la API Win32.  
  
 Puede ser un control sin ventana para ser el destino de una operación de arrastrar y colocar de OLE.  Normalmente, esto requeriría que la ventana de control está registrada como destino.  Puesto que el control no tiene ninguna ventana propio, el contenedor utiliza su propia ventana como destino.  El control proporciona una implementación de la interfaz de `IDropTarget` a la que el contenedor puede delegar llamadas en el momento adecuado.  Para exponer esta interfaz al contenedor, reemplace [COleControl::GetWindowlessDropTarget](../Topic/COleControl::GetWindowlessDropTarget.md).  Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/CPP/providing-windowless-activation_4.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)