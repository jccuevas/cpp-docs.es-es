---
title: "Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo | Documentos de Microsoft"
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
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c380d0a525c2f026054ebae1812450c4d4634c1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Contenedores de controles ActiveX: Usar controles en un contenedor sin cuadro de diálogo
En algunas aplicaciones, como un SDI o una aplicación MDI, desea incrustar un control en una ventana de la aplicación. El **crear** función miembro de la clase contenedora, insertada por Visual C++, puede crear una instancia del control dinámicamente, sin necesidad de un cuadro de diálogo.  
  
 El **crear** función miembro tiene los siguientes parámetros:  
  
 `lpszWindowName`  
 Un puntero al texto que se mostrará en la propiedad de texto o el título del control (si existe).  
  
 `dwStyle`  
 Estilos de Windows. Para obtener una lista completa, consulte [CWnd:: CreateControl](../mfc/reference/cwnd-class.md#createcontrol).  
  
 `rect`  
 Especifica el tamaño y la posición del control.  
  
 `pParentWnd`  
 Especifica la ventana del control primario, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control y puede usarse por el contenedor para hacer referencia al control.  
  
 Un ejemplo del uso de esta función para crear dinámicamente un control ActiveX sería en una vista de formulario de una aplicación SDI. A continuación, podría crear una instancia del control en el `WM_CREATE` controlador de la aplicación.  
  
 En este ejemplo, `CMyView` es la clase de vista principal, `CCirc` es la clase contenedora y CIRC. H es el encabezado (. (H) del archivo de la clase contenedora.  
  
 Implementar esta característica es un proceso de cuatro pasos.  
  
### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Para crear dinámicamente un control ActiveX en una ventana sin cuadro de diálogo  
  
1.  Inserte CIRC. H en CMYVIEW. H, justo antes del `CMyView` definición de clase:  
  
     [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]  
  
2.  Agregar una variable miembro (de tipo `CCirc`) a la sección protegida de la `CMyView` situada en CMYVIEW de definición de la clase. H:  
  
     [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]  
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]  
  
3.  Agregar un `WM_CREATE` controlador de mensajes para la clase `CMyView`.  
  
4.  En la función de controlador, `CMyView::OnCreate`, realizar una llamada para el control `Create` función utilizando la **esto** puntero como la ventana primaria:  
  
     [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]  
  
5.  Recompile el proyecto. Un control Circ se creará dinámicamente cada vez que se crea la vista de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

