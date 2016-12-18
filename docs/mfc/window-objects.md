---
title: "Window (Objetos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas de marco [C++], Window (objetos) C++"
  - "HWND"
  - "HWND, Window (objetos)"
  - "mensajes [C++], Windows"
  - "MFC [C++], ventanas"
  - "objetos [C++], ventana"
  - "Visual C++, Window (objetos)"
  - "mensajes de Windows [C++]"
  - "Window (objetos) [C++]"
  - "ventanas [C++], Window (objetos) C++"
  - "Windows (ventana) [C++]"
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Window (Objetos)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase [CWnd](../mfc/reference/cwnd-class.md) de MFC suministra para encapsular el identificador de `HWND` de una ventana.  El objeto de `CWnd` es el objeto de la ventana de c\+\+., distinto de `HWND` que representa una ventana de Windows pero contenerla.  Utilice `CWnd` para derivar dispone de clases de ventana secundaria, o utilice una de las muchas clases MFC derivadas de `CWnd`.  La clase `CWnd` es la clase base para todas las ventanas, incluidas las ventanas de marco, cuadros de diálogo, ventanas secundarias, controles, y las barras de control como barras de herramientas.  Comprender claramente de [la relación entre el objeto de la ventana de c\+\+. y un HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) es crucial para la programación eficaz con MFC.  
  
 MFC proporciona cierta funcionalidad y administración predeterminadas de ventanas, pero puede derivar dispone de la clase de `CWnd` y utilizar su funciones miembro para personalizar la funcionalidad proporcionada.  Puede crear ventanas secundarias construye un objeto de `CWnd` y llamando a la función miembro de [crear](../Topic/CWnd::Create.md) , se personalizan las ventanas secundarias mediante las funciones miembro de `CWnd` .  Puede insertar los objetos derivados de [CView](../mfc/reference/cview-class.md), como vistas de formulario o vistas de árbol, en una ventana de marco.  Y puede admitir varias vistas de los documentos a través de los paneles del divisor, proporcionadas por la clase [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Cada objeto derivado de la clase `CWnd` contiene una correspondencia de mensajes, a través de la cual puede asociar los mensajes de Windows o los id. de comando a dispone los controladores.  
  
 La literatura general en la programación para Windows es un buen recursos para obtener información sobre cómo utilizar las funciones miembro de `CWnd` , que encapsulan `HWND` API.  
  
## Funciones que se usan en un CWnd  
 `CWnd` y su [clases de ventana derivadas](../mfc/derived-window-classes.md) proporcionan constructores, destructores, y las funciones miembro para inicializar el objeto, crear estructuras subyacentes de Windows, y para tener acceso a `HWND`encapsulado.  `CWnd` también proporciona funciones miembro que encapsulan las API de Windows para enviar mensajes, tener acceso al estado de la ventana, convirtiendo coordenadas, actualizando, moviendo, teniendo acceso al portapapeles, y a muchas otras tareas.  Se encapsula la administración de ventanas API de Windows que toma un argumento de `HWND` mientras las funciones miembro de `CWnd`.  Los nombres de las funciones y sus parámetros se mantienen en la función miembro de `CWnd` .  Para obtener más información sobre las API de Windows encapsuladas por `CWnd`, vea la clase [CWnd](../mfc/reference/cwnd-class.md).  
  
## Mensajes de CWnd y Windows  
 Uno de los propósitos principales de `CWnd` es proporcionar una interfaz para administrar los mensajes de Windows, como `WM_PAINT` o `WM_MOUSEMOVE`.  Muchas de las funciones miembro de `CWnd` se controladores de los mensajes estándar — los a partir del identificador **afx\_msg** y el prefijo “on”, por ejemplo `OnPaint` y **OnMouseMove**.  mensajes y control de mensajes de cubre de[Control de mensajes y asignación](../mfc/message-handling-and-mapping.md) en detalle.  La información que se aplica por igual a las ventanas y las del marco que crea a para fines especiales.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [La relación entre el objeto de la ventana de c\+\+. y un HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Clases de ventana derivadas](../mfc/derived-window-classes.md)  
  
-   [Crear ventanas](../mfc/creating-windows.md)  
  
-   [Objetos de destrucción de la ventana](../mfc/destroying-window-objects.md)  
  
-   [Desasociar un CWnd de Su HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Trabajar con objetos de la ventana](../mfc/working-with-window-objects.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md): objetos que crean Windows que dibuja al dispositivo  
  
-   [Objetos gráficos](../mfc/graphic-objects.md): lápices, pinceles, fuentes, mapas de bits, paletas, regiones  
  
## Vea también  
 [Windows](../mfc/windows.md)