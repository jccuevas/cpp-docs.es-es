---
title: "Estilos est&#225;ticos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SS_SUNKEN"
  - "SS_CENTER"
  - "SS_ENHMETAFILE"
  - "SS_RIGHT"
  - "SS_BLACKRECT"
  - "SS_LEFTNOWORDWRAP"
  - "SS_GRAYFRAME"
  - "SS_USERITEM"
  - "SS_GRAYRECT"
  - "SS_WHITEFRAME"
  - "SS_ETCHEDFRAME"
  - "SS_ETCHEDVERT"
  - "SS_WHITERECT"
  - "SS_PATHELLIPSIS"
  - "SS_WORDELLIPSIS"
  - "SS_NOPREFIX"
  - "SS_BITMAP"
  - "SS_SIMPLE"
  - "SS_CENTERIMAGE"
  - "SS_BLACKFRAME"
  - "SS_OWNERDRAW"
  - "SS_REALSIZEIMAGE"
  - "SS_RIGHTJUST"
  - "SS_ICON"
  - "SS_NOTIFY"
  - "SS_ETCHEDHORZ"
  - "SS_LEFT"
  - "SS_ENDELLIPSIS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SS_BITMAP (constante)"
  - "SS_BLACKFRAME (constante)"
  - "SS_BLACKRECT (constante)"
  - "SS_CENTER (constante)"
  - "SS_CENTERIMAGE (constante)"
  - "SS_ENDELLIPSIS (constante)"
  - "SS_ENHMETAFILE (constante)"
  - "SS_ETCHEDFRAME (constante)"
  - "SS_ETCHEDHORZ (constante)"
  - "SS_ETCHEDVERT (constante)"
  - "SS_GRAYFRAME (constante)"
  - "SS_GRAYRECT (constante)"
  - "SS_ICON (constante)"
  - "SS_LEFT (constante)"
  - "SS_LEFTNOWORDWRAP (constante)"
  - "SS_NOPREFIX (constante)"
  - "SS_NOTIFY (constante)"
  - "SS_OWNERDRAW (constante)"
  - "SS_PATHELLIPSIS (constante)"
  - "SS_REALSIZEIMAGE (constante)"
  - "SS_RIGHT (constant)"
  - "SS_RIGHTJUST (constante)"
  - "SS_SIMPLE (constante)"
  - "SS_SUNKEN (constante)"
  - "SS_USERITEM (constante)"
  - "SS_WHITEFRAME (constante)"
  - "SS_WHITERECT (constante)"
  - "SS_WORDELLIPSIS (constante)"
  - "estilos estáticos"
ms.assetid: a1114548-fc6d-491d-8c46-21d11b8574f5
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Estilos est&#225;ticos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **SS\_BITMAP** especifica un mapa de bits debe aparecer en el control estático.  El texto determinado es el nombre de un mapa de bits \(no un nombre de archivo\) definido en otra parte del archivo de recursos.  El estilo omite los parámetros de nWidth y de nHeight; el control se ajusta para alojar el mapa de bits.  
  
-   **SS\_BLACKFRAME** especifica un cuadro con un cuadro dibujado con el mismo color que los marcos de la ventana.  El valor predeterminado es negro.  
  
-   **SS\_BLACKRECT** especifica un rectángulo relleno con un color utilizado para dibujar los marcos de la ventana.  El valor predeterminado es negro.  
  
-   **SS\_CENTER** Designates un rectángulo simple y muestra el texto especificado centrada en el rectángulo.  Se da formato al texto antes de que se muestre.  Las palabras que extenderían pasado el final de una línea automáticamente se ajustan al principio de la línea centrado siguiente.  
  
-   **SS\_CENTERIMAGE** especifica que, si el mapa de bits o icono es menor que el área de cliente del control estático, el resto del área de cliente se rellena con el color del píxel situado en la esquina superior izquierda del mapa de bits o el icono.  Si el control estático contiene una única línea de texto, el texto se centra verticalmente en el área de cliente del control.  
  
-   **SS\_ENDELLIPSIS** o **SS\_PATHELLIPSIS** reemplaza la parte de la cadena especificada con los puntos suspensivos en caso necesario, de forma que el resultado se ajuste al rectángulo especificado.  
  
     Puede especificar **SS\_END\_ELLIPSIS** para reemplazar caracteres al final de la cadena, o **SS\_PATHELLIPSIS** para reemplazar caracteres en el medio de la cadena.  Si la cadena contiene caracteres de barra diagonal inversa \(\\\), **SS\_PATHELLIPSIS** conserva tanto de texto después de la barra diagonal inversa como sea posible.  
  
-   **SS\_ENHMETAFILE** especifica un metarchivo mejorado debe aparecer en el control estático.  El texto determinado es el nombre de un metarchivo.  Un control estático de metarchivo mejorado tiene un tamaño fijo; el metarchivo se ajusta para que quepa en el área de cliente del control estático.  
  
-   **SS\_ETCHEDFRAME** dibuja el marco del control estático utilizando el estilo de borde de **EDGE\_ETCHED** .  
  
-   **SS\_ETCHEDHORZ** dibuja los bordes inferior y superior del control estático utilizando el estilo de borde de **EDGE\_ETCHED** .  
  
-   **SS\_ETCHEDVERT** dibuja los bordes izquierdo y derecho del control estático utilizando el estilo de borde de EDGE\_ETCHED.  
  
-   **SS\_GRAYFRAME** especifica un cuadro con un cuadro dibujado con el mismo color que el fondo de pantalla \(escritorio\).  El valor predeterminado es gris.  
  
-   **SS\_GRAYRECT** especifica un rectángulo relleno con un color utilizado para rellenar el fondo de la pantalla.  El valor predeterminado es gris.  
  
-   **SS\_ICON** Designates un icono mostrado en el cuadro de diálogo.  El texto determinado es el nombre de un icono \(no un nombre de archivo\) definido en otra parte del archivo de recursos.  Se omiten los parámetros de `nWidth` y de `nHeight` ; el icono automáticamente ajusta.  
  
-   **SS\_LEFT** Designates un rectángulo simple y muestra el texto especificado alineado a la izquierda del rectángulo.  Se da formato al texto antes de que se muestre.  Las palabras que extenderían pasado el final de una línea automáticamente se ajustan al principio de la línea alineado a la izquierda siguiente.  
  
-   **SS\_LEFTNOWORDWRAP** Designates un rectángulo simple y muestra el texto especificado alineado a la izquierda del rectángulo.  Se expanden las tabulaciones, pero las palabras no se encapsulan.  Texto que extiende último que el final de una línea se recorta.  
  
-   **SS\_NOPREFIX** Unless que se especifica este estilo, Windows interpreta cualquier carácter de y comercial \(&\) en el texto del control para ser caracteres de prefijo de aceleradores.  En este caso, se quita la y comercial y el siguiente carácter en la cadena aparece subrayado.  Si un control estático es contener texto donde esta característica no se desea, **SS\_NOPREFIX** puede agregarse.  Este estilo de la estático\- CONTROL se puede incluir con controles estáticos definido cualquiera de los.  Puede combinar **SS\_NOPREFIX** con otros estilos mediante el OR bit a bit el operador.  Esto se utiliza más frecuentemente para cuando los nombres de archivo u otras cadenas que pueden contener una necesidad de y comercial de mostrarse en un control estático en un cuadro de diálogo.  
  
-   **SS\_NOTIFY** Sends la ventana primaria **STN\_CLICKED**, mensajes de notificación de **STN\_DBLCLK**, de **STN\_DISABLE**, y de **STN\_ENABLE** cuando el usuario hace clic en o haga doble clic en el control.  
  
-   **SS\_OWNERDRAW** especifica que el propietario de control estático es responsable de dibujar el control.  La ventana propietaria recibe un mensaje de `WM_DRAWITEM` siempre que el control tenga debe dibujar.  
  
-   **SS\_REALSIZEIMAGE** impide que un control estático de icono o mapas de bits \(es decir, los controles estáticos que tienen el estilo de **SS\_ICON** o de **SS\_BITMAP** \) se cambie el tamaño mientras se carga o dibujado.  Si el icono o mapa de bits es mayor que el área de destino, la imagen se recorta.  
  
-   **SS\_RIGHT** Designates un rectángulo simple y muestra el texto especificado alineado a la derecha del rectángulo.  Se da formato al texto antes de que se muestre.  Las palabras que extenderían pasado el final de una línea automáticamente se ajustan al principio de la línea alineado a la derecha siguiente.  
  
-   **SS\_RIGHTJUST** especifica que la esquina inferior derecha de un control estático con el estilo de **SS\_BITMAP** o de **SS\_ICON** es permanecer fija cuando se cambia el tamaño del control.  Sólo los lados superior e izquierdo se ajustan para adaptarse a un nuevo mapa de bits o icono.  
  
-   **SS\_SIMPLE** Designates un rectángulo simple y muestra una línea de texto alineado a la izquierda del rectángulo.  La línea de texto no se puede reducir o modificar de forma alguna. \(La ventana primaria o el cuadro de diálogo control de no debe procesar el mensaje de `WM_CTLCOLOR` .\)  
  
-   **SS\_SUNKEN** dibuja un borde mitad\- hundido alrededor de un control estático.  
  
-   **SS\_USERITEM** especifica un elemento definido por el usuario.  
  
-   **SS\_WHITEFRAME** especifica un cuadro con un cuadro dibujado con el mismo color que el fondo de la ventana.  El valor predeterminado es blanco.  
  
-   **SS\_WHITERECT** especifica un rectángulo relleno con un color utilizado para rellenar el fondo de la ventana.  El valor predeterminado es blanco.  
  
-   **SS\_WORDELLIPSIS** trunca el texto no quepa y agrega elipses.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CStatic::Create](../Topic/CStatic::Create.md)   
 [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)   
 [Static Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb760773)