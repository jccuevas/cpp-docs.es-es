---
title: "Estilos de ventana extendidos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WS_EX_TOOLWINDOW"
  - "WS_EX_LEFTSCROLLBAR"
  - "WS_EX_RTLREADING"
  - "WS_EX_WINDOWEDGE"
  - "WS_EX_CLIENTEDGE"
  - "WS_EX_STATICEDGE"
  - "WS_EX_LTRREADING"
  - "WS_EX_DLGMODALFRAME"
  - "WS_EX_RIGHTSCROLLBAR"
  - "WS_EX_CONTROLPARENT"
  - "WS_EX_ACCEPTFILES"
  - "WS_EX_TRANSPARENT"
  - "WS_EX_RIGHT"
  - "WS_EX_APPWINDOW"
  - "WS_EX_TOPMOST"
  - "WS_EX_CONTEXTHELP"
  - "WS_EX_MDICHILD"
  - "WS_EX_LEFT"
  - "WS_EX_OVERLAPPEDWINDOW"
  - "WS_EX_PALETTEWINDOW"
  - "WS_EX_NOPARENTNOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estilos de ventana extendidos"
  - "estilos, ventanas"
  - "WS_EX_ACCEPTFILES (constante)"
  - "WS_EX_APPWINDOW (constante)"
  - "WS_EX_CLIENTEDGE (constante)"
  - "WS_EX_CONTEXTHELP (constante)"
  - "WS_EX_CONTROLPARENT (constante)"
  - "WS_EX_DLGMODALFRAME (constante)"
  - "WS_EX_LEFT (constante)"
  - "WS_EX_LEFTSCROLLBAR (constante)"
  - "WS_EX_LTRREADING (constante)"
  - "WS_EX_MDICHILD (constante)"
  - "WS_EX_NOPARENTNOTIFY (constante)"
  - "WS_EX_OVERLAPPEDWINDOW (constante)"
  - "WS_EX_PALETTEWINDOW (constante)"
  - "WS_EX_RIGHT (constante)"
  - "WS_EX_RIGHTSCROLLBAR (constante)"
  - "WS_EX_RTLREADING (constante)"
  - "WS_EX_STATICEDGE (constante)"
  - "WS_EX_TOOLWINDOW (constante)"
  - "WS_EX_TOPMOST (constante)"
  - "WS_EX_TRANSPARENT (constante)"
  - "WS_EX_WINDOWEDGE (constante)"
ms.assetid: d18e6c69-0a01-49ed-b58a-55b3802b47c1
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Estilos de ventana extendidos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **WS\_EX\_ACCEPTFILES** Especifica que una ventana creada con este estilo acepta arrastrar y colocar archivos.  
  
-   **WS\_EX\_APPWINDOW** Fuerza una ventana de nivel superior sobre la barra de tareas cuando la ventana está visible.  
  
-   **WS\_EX\_CLIENTEDGE** Especifica que una ventana tiene un aspecto 3D, es decir, el borde tiene el filo hundido.  
  
-   **WS\_EX\_CONTEXTHELP** Incluye un signo de interrogación en la barra de título de la ventana.  Cuando el usuario hace clic en el signo de interrogación, el cursor se transforma en un signo de interrogación con un puntero.  Si, a continuación, el usuario hace clic en una ventana secundaria, esta recibe un mensaje **WM\_HELP**.  
  
-   **WS\_EX\_CONTROLPARENT** Permite al usuario navegar entre las ventanas secundarias mediante la tecla TAB.  
  
-   **WS\_EX\_DLGMODALFRAME** Designa una ventana con un borde doble que puede crearse \(opcionalmente\) con una barra de título cuando se especifica la marca de estilo **WS\_CAPTION** en el parámetro `dwStyle`.  
  
-   **WS\_EX\_LAYERED** Especifica que se trata de una [ventana por capas](http://msdn.microsoft.com/library/ms632599\(v=vs.85\).aspx#layered").  Este estilo no se puede utilizar si la ventana tiene un [estilo de clase](http://msdn.microsoft.com/library/ms633574\(v=vs.85\).aspx#class_styles") de **CS\_OWNDC** o **CS\_CLASSDC**.  Sin embargo, [!INCLUDE[win8_first](../../mfc/reference/includes/win8_first_md.md)] admite el estilo **WS\_EX\_LAYERED** para las ventanas secundarias en casos donde las versiones anteriores de Windows solo lo admitían para las ventanas de nivel superior.  
  
-   **WS\_EX\_LEFT** Proporciona propiedades genéricas de ventana alineada a la izquierda.  Éste es el valor predeterminado.  
  
-   **WS\_EX\_LEFTSCROLLBAR** Coloca una barra de desplazamiento vertical a la izquierda del área cliente.  
  
-   **WS\_EX\_LTRREADING** Muestra el texto de la ventana con propiedades de orden de lectura de izquierda a derecha.  Éste es el valor predeterminado.  
  
-   **WS\_EX\_MDICHILD** Crea una ventana secundaria MDI.  
  
-   **WS\_EX\_NOPARENTNOTIFY** Especifica que una ventana secundaria creada con este estilo no enviará el mensaje `WM_PARENTNOTIFY` a su ventana primaria cuando se cree o se destruya la ventana secundaria.  
  
-   **WS\_EX\_OVERLAPPEDWINDOW** Combina los estilos **WS\_EX\_CLIENTEDGE** y **WS\_EX\_WINDOWEDGE**.  
  
-   **WS\_EX\_PALETTEWINDOW** Combina los estilos **WS\_EX\_WINDOWEDGE** y **WS\_EX\_TOPMOST**.  
  
-   **WS\_EX\_RIGHT** Proporciona propiedades genéricas de ventana alineada a la derecha.  Esto depende de la clase de ventana.  
  
-   **WS\_EX\_RIGHTSCROLLBAR** Coloca una barra de desplazamiento vertical \(si existe\) a la derecha del área cliente.  Éste es el valor predeterminado.  
  
-   **WS\_EX\_RTLREADING** Muestra el texto de la ventana con propiedades de orden de lectura de derecha a izquierda.  
  
-   **WS\_EX\_STATICEDGE** Crea una ventana con un estilo de borde tridimensional diseñado para usarlo con elementos que no aceptan datos proporcionados por el usuario.  
  
-   **WS\_EX\_TOOLWINDOW** Crea una ventana de herramientas, que es una ventana diseñada para usarla como barra de herramientas flotante.  Una ventana de herramientas tiene una barra de título más corta que una normal y el título de la ventana se dibuja con una fuente menor.  Una ventana de herramientas no aparece en la barra de tareas ni en la ventana que se muestra cuando el usuario presiona ALT\+TAB.  
  
-   **WS\_EX\_TOPMOST** Especifica que una ventana creada con este estilo debe colocarse encima de las ventanas que no son de nivel superior y debe mantenerse encima de ellas incluso cuando se desactiva.  Una aplicación puede utilizar la función miembro `SetWindowPos` para agregar o quitar este atributo.  
  
-   **WS\_EX\_TRANSPARENT** Especifica que una ventana creada con este estilo debe ser transparente.  Es decir, la ventana no tapa ninguna de las ventanas que estén debajo.  Una ventana creada con este estilo solo recibe los mensajes `WM_PAINT` después de que todas las ventanas del mismo nivel que estén debajo se hayan actualizado.  
  
-   **WS\_EX\_WINDOWEDGE** Especifica que una ventana tiene el borde en relieve.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)   
 [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)