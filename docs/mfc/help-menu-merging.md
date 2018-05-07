---
title: Combinar el menú Ayuda | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce8d5212f78546c08734aed6fd7e236fa4446007
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="help-menu-merging"></a>Combinar el menú Ayuda
Cuando un objeto está activo dentro de un contenedor, el menú combinación de protocolo de documentos OLE proporciona el objeto control total sobre la **ayuda** menú. Como resultado, los temas de Ayuda del contenedor no están disponibles a menos que el usuario desactiva el objeto. La arquitectura de contención de documentos activos se expande en las reglas de combinación para permitir que el contenedor y un documento activo que está activo para compartir el menú de menús en contexto. Las nuevas reglas son simples normas adicionales acerca de qué componente es propietario de qué parte del menú y cómo se crea el menú compartido.  
  
 La nueva convención es sencilla. En documentos activos, el **ayuda** menú tiene dos elementos de menú de nivel superior que se organiza del siguiente modo:  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 Por ejemplo, cuando una sección de Word está activa en el cuaderno de Office, la **ayuda** menú podría aparecer como sigue:  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 Ambos elementos de menú son menús en cascada en la que se proporcionan los elementos de menú adicionales específicos para el contenedor y el objeto al usuario. ¿Qué elementos aparecen aquí variarán con los contenedores y objetos implicados.  
  
 Para construir este combinado **ayuda** menú, la arquitectura de contención de documentos activos modifica el procedimiento normal de documentos OLE. Según los documentos OLE, la barra de menús combinados puede tener seis grupos de menús, es decir, **archivo**, **editar**, **contenedor**, `Object`, **ventana**, **Ayuda**, en ese orden. En cada grupo, puede haber cero o más de los menús. Los grupos de **archivo**, **contenedor**, y **ventana** pertenece al contenedor y los grupos de **editar**, **(objeto),** y **ayuda** pertenecen al objeto. Cuando el objeto desea combinar menús, crea una barra de menús en blanco y lo pasa al contenedor. El contenedor, a continuación, inserta sus menús, mediante una llamada a **IOleInPlaceFrame::InsertMenus**. El objeto también pasa una estructura que es una matriz de seis valores LARGOS (**OLEMENUGROUPWIDTHS**). Después de insertar los menús, el contenedor marca cuántos menús agregó a cada uno de sus grupos y, a continuación, se devuelve. A continuación, el objeto inserta sus menús, preste atención al recuento de los menús de cada grupo contenedor. Por último, el objeto pasa la barra de menús combinados y la matriz (que contiene el recuento de los menús de cada grupo) a OLE, que devuelve un opaco "descriptor de menú" controlar. Más adelante el objeto pasa el identificador y la barra de menús combinados al contenedor, y a través de **IOleInPlaceFrame:: SetMenu**. En este momento, el contenedor muestra la barra de menús combinados y pasará el identificador a OLE, por lo que OLE pueda enviar correctamente los mensajes de menús.  
  
 En el procedimiento de documento activo modificado, el objeto debe inicializar primero el **OLEMENUGROUPWIDTHS** elementos a cero antes de pasarlos al contenedor. A continuación, el contenedor realiza una inserción de menú normal con una excepción: las inserciones de contenedor un **ayuda** menú como el último elemento y almacena el valor 1 en la última (sexta) entrada de la **OLEMENUGROUPWIDTHS** matriz (es decir, width [5], que pertenece al grupo ayuda del objeto). Esto **ayuda** menú tendrá solo un elemento que es un submenú, el "**contenedor ayuda** >" menú en cascada como se describió anteriormente.  
  
 A continuación, ejecuta el objeto de su código de inserción normal de menús, salvo que antes de insertar su **ayuda** menú, comprueba la sexta entrada de la **OLEMENUGROUPWIDTHS** matriz. Si el valor es 1 y el nombre del último menú es **ayuda** (o cadena traducida adecuado), a continuación, inserta el objeto su **ayuda** menú como submenú del contenedor **ayuda** menú.  
  
 El objeto, a continuación, Establece el sexto elemento de **OLEMENUGROUPWIDTHS** a cero e incrementa el quinto elemento por uno. Esto permite a OLE saber que el **ayuda** menú pertenece al contenedor y se deberían enrutar los mensajes de menú correspondiente a ese menú (y sus submenús) en el contenedor. A continuación, es responsabilidad del contenedor para reenviar `WM_INITMENUPOPUP`, **WM_SELECT**, **WM_COMMAND**y otros mensajes relacionados con el menú que pertenecen a la parte del objeto de la **ayuda**  menú. Esto se logra mediante el uso de `WM_INITMENU` para borrar una marca que indique el contenedor si el usuario haya navegado en el objeto **ayuda** menú. A continuación, supervisa el contenedor `WM_MENUSELECT` para entrada o salida de cualquier elemento en el **ayuda** menú que no haya agregado el contenedor. En la entrada, significa que el usuario haya navegado a un menú del objeto, por lo que el contenedor establece la marca "en el menú de Ayuda del objeto" y el estado de dicha marca utiliza para reenviar cualquier `WM_MENUSELECT`, `WM_INITMENUPOPUP`, y **WM_COMMAND** mensajes, como mínimo, a la ventana de objetos. (Al salir, el contenedor borra la marca y, a continuación, procesa estos mismos mensajes de sí mismo.) El contenedor debe utilizar la ventana devuelta desde el objeto **IOleInPlaceActiveObejct:: GetWindow** funcionar como el destino de estos mensajes.  
  
 Si el objeto detecta un valor cero en el sexto elemento de **OLEMENUGROUPWIDTHS**, continúa de acuerdo con las reglas normales de documentos OLE. Este procedimiento explica los contenedores que participan en **ayuda** menú Combinar, así como los que no tienen que serlo.  
  
 Cuando el objeto llama **IOleInPlaceFrame:: SetMenu**, antes de mostrar el menú combinado de la barra, las comprobaciones de contenedor si el **ayuda** menú tiene un submenú adicional, además de lo que tiene el contenedor Insertar. Si por lo tanto, el contenedor dejará su **ayuda** menú en la barra de menús combinados. Si el **ayuda** menú no tiene un submenú adicional, el contenedor quitará su **ayuda** menú en la barra de menú combinado. Este procedimiento aplica a los objetos que participan en **ayuda** menú Combinar, así como los que no tienen que serlo.  
  
 Por último, cuando llega el momento para desensamblar el menú, el objeto quita las filas insertadas **ayuda** menú además de quitar la otra inserta los menús. Cuando el contenedor quita sus menús, se quitarán sus **ayuda** menú además de los otros menús que se han insertado.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de documentos activos](../mfc/active-document-containers.md)

