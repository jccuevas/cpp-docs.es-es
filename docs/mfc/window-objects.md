---
title: Window (objetos) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63b8d8dbde679d030eddd77fae6ca1fab519fdac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="window-objects"></a>Window (Objetos)
MFC proporciona la clase [CWnd](../mfc/reference/cwnd-class.md) para encapsular la `HWND` identificador de una ventana. El `CWnd` objeto es un objeto de ventana de C++ distinto de la `HWND` que representa una ventana de ventana, pero que lo contiene. Usar `CWnd` derivar su propia ventana secundaria clases o utilice una de las muchas clases MFC derivados `CWnd`. Clase `CWnd` es la clase base para todas las ventanas, incluidas las barras de control, como las barras de herramientas, cuadros de diálogo, ventanas secundarias, controles y ventanas de marco. Un buen conocimiento de [la relación entre un objeto de ventana de C++ y un HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) es fundamental para la programación eficaz con MFC.  
  
 MFC proporciona cierta funcionalidad predeterminada y la administración de windows, pero puede derivar su propia clase de `CWnd` y utilizar sus funciones miembro para personalizar la funcionalidad proporcionada. Puede crear ventanas secundarias mediante la creación de un `CWnd` objeto y llamar a su [crear](../mfc/reference/cwnd-class.md#create) miembro función, a continuación, personalizar las ventanas secundarias mediante `CWnd` funciones miembro. Puede incrustar objetos derivados de [CView](../mfc/reference/cview-class.md), como vistas de formulario o vistas de árbol, en una ventana de marco. Y puede admitir varias vistas de los documentos a través de paneles de divisor, proporcionados por la clase [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Cada objeto derivado de la clase `CWnd` contiene un mapa de mensajes, a través del cual puede asignar mensajes de Windows o identificadores de comando a sus propios controladores.  
  
 La documentación general acerca de la programación para Windows es un buen recurso para aprender a utilizar el `CWnd` funciones de miembro, que encapsulan la `HWND` API.  
  
## <a name="functions-for-operating-on-a-cwnd"></a>Funciones para trabajar de un objeto CWnd  
 `CWnd` y su [las clases de ventana derivadas](../mfc/derived-window-classes.md) proporcionan constructores, destructores y funciones miembro para inicializar el objeto, crean las estructuras subyacentes de Windows y tener acceso a encapsulado `HWND`. `CWnd` También proporciona funciones miembro que encapsulan las API de Windows para enviar mensajes, tener acceso a estado de la ventana, convertir coordenadas, actualizar, desplazarse, tener acceso al Portapapeles y muchas otras tareas. La mayoría de las API de administración de ventanas de Windows que llevar a cabo una `HWND` argumento se encapsulan como funciones miembro de `CWnd`. Los nombres de las funciones y sus parámetros se conservan en el `CWnd` función miembro. Para obtener más información acerca de las API de Windows encapsuladas por `CWnd`, vea la clase [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="cwnd-and-windows-messages"></a>CWnd y mensajes de Windows  
 Uno de los principales objetivos de `CWnd` es proporcionar una interfaz para controlar mensajes de Windows, como `WM_PAINT` o `WM_MOUSEMOVE`. Muchas de las funciones miembro de `CWnd` son controladores para mensajes estándares, los que empiezan con el identificador **afx_msg** y el prefijo "On", como `OnPaint` y **OnMouseMove**. [Control y asignación de mensajes](../mfc/message-handling-and-mapping.md) sobre mensajes y control de mensajes en detalle. Esta información se aplica igualmente a windows del marco de trabajo y los que el usuario crea para fines especiales.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [La relación entre un objeto de ventana de C++ y un HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Clases de ventana derivadas](../mfc/derived-window-classes.md)  
  
-   [Crear ventanas](../mfc/creating-windows.md)  
  
-   [Destruir objetos window](../mfc/destroying-window-objects.md)  
  
-   [Desasociación de CWnd de su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Trabajar con objetos window](../mfc/working-with-window-objects.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md): objetos que permiten dibujar dispositivo en Windows independiente  
  
-   [Objetos gráficos](../mfc/graphic-objects.md): lápices, pinceles, fuentes, mapas de bits, paletas, regiones  
  
## <a name="see-also"></a>Vea también  
 [Windows](../mfc/windows.md)

