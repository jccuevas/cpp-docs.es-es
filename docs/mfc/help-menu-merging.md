---
title: "Combinar el men&#250; Ayuda | Microsoft Docs"
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
  - "menús, combinar"
  - "combinar menús Ayuda"
  - "Ayuda, para contenedores de documentos activos"
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Combinar el men&#250; Ayuda
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un objeto se activa dentro de un contenedor, el menú que combina el protocolo de documentos de OLE proporciona un control total del menú de **Ay&uda** .  Como resultado, los temas de Ayuda del contenedor no están disponibles a menos que el usuario desactive el objeto.  La arquitectura de contención de documento activo expande las reglas para el menú de contexto que se combina para permitir el contenedor y un documento activo que está activo compartir el menú.  Las nuevas reglas son convenciones simplemente adicionales sobre qué componente posee qué parte del menú y cómo se construye el menú compartido.  
  
 La nueva convención es simple.  En documentos activos, el menú de **Ay&uda** tiene dos elementos de menú de nivel superior organizados como sigue:  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 Por ejemplo, cuando una sección de word está activo en el enlazador de Office, el menú de **Ay&uda** aparecería como sigue:  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 Ambos elementos de menú son menús en cascada en los que un elemento de menú adicional específico del contenedor y el objeto se proporciona al usuario.  Aparecen los elementos aquí variará con el contenedor y los objetos implicados.  
  
 Para generar este menú combinado de **Ay&uda** , la arquitectura de contención de documento activo modifica el procedimiento OLE normal de los documentos.  Como documentos de OLE, la barra de menú combinado puede tener seis grupos de menús, a saber **archivo**, **edición**, **Contenedor**, `Object`, **Ventana**, **Ay&uda**, en ese orden.  En cada grupo, puede tener cero o más menú.  Los grupos **archivo**, **Contenedor**, y **Ventana** pertenecen al contenedor y grupos **edición**, **Object,** y **Ay&uda** pertenecen al objeto.  Cuando el objeto desea hacer el menú que se combina, crea una barra de menús en blanco y la pasa al contenedor.  El contenedor a continuación inserta sus menús, llamando a **IOleInPlaceFrame::InsertMenus**.  El objeto también pasa una estructura que es una matriz de seis valores de LONG \(**OLEMENUGROUPWIDTHS**\).  Después de insertar los menús, el contenedor marca cuántos menús agregado en cada uno de los grupos, y vuelve.  El objeto inserta sus menús, prestando atención al recuento de menús en cada grupo de contenedor.  Finalmente, el objeto pasa la barra de menú combinado y la matriz \(que contiene el recuento de menús en cada grupo\) OLE, que devuelve “un identificador opaco de descriptor de menú”.  El objeto pasa más tarde ese identificador y la barra de menú combinado al contenedor, mediante **IOleInPlaceFrame::SetMenu**.  En este momento, el contenedor muestra la barra de menú combinado y también pasa el identificador a OLE, de modo que OLE puede hacer enviar adecuado de los mensajes del menú.  
  
 En el procedimiento modificado del documento activo, el objeto debe inicializar los elementos de **OLEMENUGROUPWIDTHS** a cero antes de pasarlo al contenedor.  El contenedor realiza una inserción normal de menú con una excepción: El contenedor inserta un menú de **Ay&uda** como el último elemento y almacena el valor 1 en \(la sexta\) última entrada de la matriz de **OLEMENUGROUPWIDTHS** \(es decir, ancho \[5\], que pertenece al grupo de Ayuda de objeto\).  Este menú de **Ay&uda** sólo tendrá un elemento que es un submenú, el menú en cascada de “**Container Help** \>” como se describió anteriormente.  
  
 El objeto continuación ejecuta el código normal de la inserción de menú, salvo que antes de insertar el menú de **Ay&uda** , comprueba la sexta entrada de matriz de **OLEMENUGROUPWIDTHS** .  Si el valor es 1 y el nombre del menú pasado es **Ay&uda** \(o la cadena adaptada adecuada\), el objeto inserta el menú de **Ay&uda** como submenú del menú de **Ay&uda** del contenedor.  
  
 El objeto establezca el sexto elemento de **OLEMENUGROUPWIDTHS** a cero y aumenta el quinto elemento por uno.  Esto permite OLE saber que el menú de **Ay&uda** pertenece al contenedor y mensajes de menú correspondiente a ese menú \(y sus submenús\) deben enrutar al contenedor.  A continuación es responsabilidad del contenedor reenviar `WM_INITMENUPOPUP`, **WM\_SELECT**, **WM\_COMMAND**, y otros mensajes menú\- relacionados que pertenecen a la parte del menú de **Ay&uda** .  Esto se logra mediante `WM_INITMENU` borrar un marcador que indica el contenedor si el usuario navegue por el menú de **Ay&uda** del objeto.  El contenedor a observa `WM_MENUSELECT` para la entrada en la salida de cualquier elemento del menú de **Ay&uda** que el contenedor no agregó propio.  En la entrada, significa que el usuario ha navegado en un menú object, por lo que el contenedor establece “en el indicador del menú ayuda de objetos” y usa el estado del indicador para reenviar cualquier `WM_MENUSELECT`, `WM_INITMENUPOPUP`, y los mensajes de **WM\_COMMAND** , como mínimo, en la ventana del objeto. \(En la salida, el contenedor borra el indicador y después procesa estos mismos mensajes propio\). El contenedor debe utilizar la ventana devuelta por la función de **IOleInPlaceActiveObejct::GetWindow** de objeto como destino para estos mensajes.  
  
 Si el objeto detecta un cero en el sexto elemento de **OLEMENUGROUPWIDTHS**, continúa como documentos las reglas VIEJAS habituales.  Este procedimiento se tratan los contenedores que participan en el menú de **Ay&uda** que se combina con los que no lo hacen.  
  
 Cuando el objeto llama **IOleInPlaceFrame::SetMenu**, antes de mostrar la barra de menú combinado, el contenedor comprueba si el menú de **Ay&uda** tiene un submenú adicional, además de lo que ha insertado el contenedor.  Si es así el contenedor permite el menú de **Ay&uda** en la barra de menú combinado.  Si el menú de **Ay&uda** no tiene un submenú adicional, el contenedor quitará el menú de **Ay&uda** de la barra de menú combinado.  Este procedimiento se tratan los objetos que participan en el menú de **Ay&uda** que se combina con los que no lo hacen.  
  
 Finalmente, cuando llega el momento de desensamblar el menú, el objeto quita el menú insertado de **Ay&uda** además de quitar los otros menús incrustados.  Cuando el contenedor quita los menús, quitará el menú de **Ay&uda** además de los otros menús que ha insertado.  
  
## Vea también  
 [Contenedores de documentos activos](../mfc/active-document-containers.md)