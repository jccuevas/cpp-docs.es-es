---
title: "Estilos estáticos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SS_SUNKEN
- SS_CENTER
- SS_ENHMETAFILE
- SS_RIGHT
- SS_BLACKRECT
- SS_LEFTNOWORDWRAP
- SS_GRAYFRAME
- SS_USERITEM
- SS_GRAYRECT
- SS_WHITEFRAME
- SS_ETCHEDFRAME
- SS_ETCHEDVERT
- SS_WHITERECT
- SS_PATHELLIPSIS
- SS_WORDELLIPSIS
- SS_NOPREFIX
- SS_BITMAP
- SS_SIMPLE
- SS_CENTERIMAGE
- SS_BLACKFRAME
- SS_OWNERDRAW
- SS_REALSIZEIMAGE
- SS_RIGHTJUST
- SS_ICON
- SS_NOTIFY
- SS_ETCHEDHORZ
- SS_LEFT
- SS_ENDELLIPSIS
dev_langs:
- C++
helpviewer_keywords:
- SS_ICON constant
- SS_WHITEFRAME constant
- SS_BLACKFRAME constant
- SS_ETCHEDHORZ constant
- SS_OWNERDRAW constant
- SS_BITMAP constant
- SS_NOPREFIX constant
- SS_NOTIFY constant
- SS_CENTER constant
- SS_REALSIZEIMAGE constant
- SS_ETCHEDFRAME constant
- SS_CENTERIMAGE constant
- SS_SUNKEN constant
- SS_ENDELLIPSIS constant
- SS_WORDELLIPSIS constant
- SS_WHITERECT constant
- SS_ETCHEDVERT constant
- SS_GRAYFRAME constant
- SS_LEFTNOWORDWRAP constant
- SS_LEFT constant
- SS_SIMPLE constant
- static styles
- SS_ENHMETAFILE constant
- SS_GRAYRECT constant
- SS_USERITEM constant
- SS_PATHELLIPSIS constant
- SS_BLACKRECT constant
- SS_RIGHT constant
- SS_RIGHTJUST constant
ms.assetid: a1114548-fc6d-491d-8c46-21d11b8574f5
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ad34c688fdfd3c2b4c81a0a03fbce53a905162ad
ms.lasthandoff: 02/24/2017

---
# <a name="static-styles"></a>Estilos estáticos
-   **SS_BITMAP** especifica un mapa de bits se mostrará en el control estático. El texto especificado es el nombre de un mapa de bits (no un nombre de archivo) definido en otra parte del archivo de recursos. El estilo omite los parámetros nWidth y nHeight; el control se ajusta automáticamente para alojar el mapa de bits.  
  
-   **SS_BLACKFRAME** especifica un cuadro con un marco que se dibuja con el mismo color que marcos de ventana. El valor predeterminado es negro.  
  
-   **SS_BLACKRECT** especifica un rectángulo rellenado con el color usado para dibujar los marcos de ventana. El valor predeterminado es negro.  
  
-   **SS_CENTER** designa un rectángulo simple y muestra el texto dado centrado en el rectángulo. El texto tiene formato antes de que se muestre. Palabras que se extienden más allá del final de una línea se ajustan automáticamente al principio de la siguiente línea centrado.  
  
-   **SS_CENTERIMAGE** especifica que, si el icono o mapa de bits es menor que el área de cliente del control estático, el resto del área de cliente se rellena con el color del píxel de la esquina superior izquierda del mapa de bits o icono. Si el control estático contiene una sola línea de texto, el texto se centra verticalmente en el área cliente del control.  
  
-   **SS_ENDELLIPSIS** o **SS_PATHELLIPSIS** reemplaza parte de la cadena especificada con los puntos suspensivos, si es necesario, para que quepa el resultado en el rectángulo especificado.  
  
     Puede especificar **SS_END_ELLIPSIS** para reemplazar caracteres al final de la cadena, o **SS_PATHELLIPSIS** para reemplazar caracteres dentro de la cadena. Si la cadena contiene la barra diagonal inversa (\\) caracteres, **SS_PATHELLIPSIS** conserva como parte del texto después de la última barra diagonal inversa como sea posible.  
  
-   **SS_ENHMETAFILE** especifica un metarchivo mejorado se mostrarán en el control estático. El texto especificado es el nombre de un metarchivo. Un control estático de metarchivo mejorado tiene un tamaño fijo; metarchivo se escala para ajustar el área cliente del control estático.  
  
-   **SS_ETCHEDFRAME** dibuja el marco del control estático mediante el **EDGE_ETCHED** estilo de borde.  
  
-   **SS_ETCHEDHORZ** dibuja los bordes superior e inferior del control estático mediante el **EDGE_ETCHED** estilo de borde.  
  
-   **SS_ETCHEDVERT** dibuja los bordes izquierdos y derecho del control estático utilizando el estilo de borde EDGE_ETCHED.  
  
-   **SS_GRAYFRAME** especifica un cuadro con un marco que se dibuja con el mismo color que el fondo de la pantalla (escritorio). El valor predeterminado es gris.  
  
-   **SS_GRAYRECT** especifica un rectángulo rellenado con el color usado para rellenar el fondo de la pantalla. El valor predeterminado es gris.  
  
-   **SS_ICON** designa un icono que se muestra en el cuadro de diálogo. El texto especificado es el nombre de un icono (no un nombre de archivo) definido en otra parte del archivo de recursos. El `nWidth` y `nHeight` se omiten los parámetros; el icono ajusta su tamaño automáticamente.  
  
-   **SS_LEFT** designa un rectángulo simple y muestra el vaciado izquierda del rectángulo de texto dado. El texto tiene formato antes de que se muestre. Palabras que se extienden más allá del final de una línea se ajustan automáticamente al principio de la línea siguiente de la izquierda de vaciado.  
  
-   **SS_LEFTNOWORDWRAP** designa un rectángulo simple y muestra el vaciado izquierda del rectángulo de texto dado. Se expanden las fichas, pero no se ajustan palabras. Se recorta el texto que se extiende más allá del final de una línea.  
  
-   **SS_NOPREFIX** a menos que se especifique este estilo, Windows interpretará los caracteres y comercial (&) en el texto del control de caracteres de prefijo del acelerador. En este caso, se quita la y comercial, y se subraya el carácter siguiente de la cadena. Si un control estático es contener el texto que no se desea esta característica, **SS_NOPREFIX** pueden agregarse. Este estilo de control estático puede incluir cualquiera de los controles estáticos definidos. Puede combinar **SS_NOPREFIX** con otros estilos mediante el operador OR bit a bit. Esto se suele utilizar cuando los nombres de archivo u otras cadenas que pueden contener una y comercial que se muestra en un control estático en un cuadro de diálogo.  
  
-   **SS_NOTIFY** envía la ventana primaria **STN_CLICKED**, **STN_DBLCLK**, **STN_DISABLE**, y **STN_ENABLE** mensajes de notificación cuando el usuario hace clic o doble clic en el control.  
  
-   **SS_OWNERDRAW** especifica que el propietario del control estático es responsable de dibujar el control. La ventana propietaria recibe un `WM_DRAWITEM` mensaje cada vez que el control debe dibujarse.  
  
-   **SS_REALSIZEIMAGE** impide que un control estático de icono o mapa de bits (es decir, los controles estáticos que tienen la **SS_ICON** o **SS_BITMAP** estilo) de tamaño cuando se cargan o se dibujan. Si el icono o mapa de bits es mayor que el área de destino, se recorta la imagen.  
  
-   **SS_RIGHT** designa un rectángulo simple y muestra el texto dado derecho de vaciado en el rectángulo. El texto tiene formato antes de que se muestre. Palabras que se extienden más allá del final de una línea se ajustan automáticamente al principio de la línea siguiente de la derecha de vaciado.  
  
-   **SS_RIGHTJUST** que especifica la esquina inferior derecha de un control estático con el **SS_BITMAP** o **SS_ICON** estilo es permanezca fijo cuando el control cambia de tamaño. Los lados superiores e izquierdos se ajustan para dar cabida a un nuevo mapa de bits o icono.  
  
-   **SS_SIMPLE** designa un rectángulo simple y se muestra una sola línea de texto vaciado izquierda del rectángulo. La línea de texto no puede ser acortan o modifica de alguna forma. (Cuadro de diálogo o ventana primaria del control no debe procesar el `WM_CTLCOLOR` mensaje.)  
  
-   **SS_SUNKEN** dibuja un borde de bajo relieve alrededor de un control estático.  
  
-   **SS_USERITEM** especifica un elemento definido por el usuario.  
  
-   **SS_WHITEFRAME** especifica un cuadro con un marco que se dibuja con el mismo color que el fondo de la ventana. El valor predeterminado es blanco.  
  
-   **SS_WHITERECT** especifica un rectángulo rellenado con el color usado para rellenar el fondo de la ventana. El valor predeterminado es blanco.  
  
-   **SS_WORDELLIPSIS** trunca el texto que no se ajusta y agrega puntos suspensivos.  
  
## <a name="see-also"></a>Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CStatic::Create](../../mfc/reference/cstatic-class.md#create)   
 [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)   
 [Estilos de Control estático](http://msdn.microsoft.com/library/windows/desktop/bb760773)


