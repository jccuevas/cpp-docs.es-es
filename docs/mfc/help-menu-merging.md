---
title: Combinar el menú Ayuda
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: 3db635cfdc39f9c4166bbf3d6958f52e535d91f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578534"
---
# <a name="help-menu-merging"></a>Combinar el menú Ayuda

Cuando un objeto está activo dentro de un contenedor, el protocolo de documentos OLE de combinación de menús proporciona el objeto control total sobre la **ayuda** menú. Como resultado, los temas de Ayuda del contenedor no están disponibles a menos que el usuario desactiva el objeto. La arquitectura de contención de documentos activos se expande en las reglas de combinación para permitir que el contenedor y un documento activo en el que está activo para compartir el menú de menús en contexto. Las reglas nuevas son convenciones simplemente adicionales acerca de qué componente posee qué parte del menú y cómo se construye el menú compartido.

La nueva convención es sencilla. En los documentos activos, el **ayuda** menú tiene dos elementos de menú de nivel superior que se organizan del siguiente modo:

`Help`

`Container Help >`

`Object Help    >`

Por ejemplo, cuando el proceso de una sección de Word está activa en el cuaderno de Office, el **ayuda** menú podría aparecer como sigue:

`Help`

`Binder Help >`

`Word Help   >`

Ambos elementos de menú son menús en cascada en la que se proporcionan los elementos de menú adicionales específicos para el contenedor y el objeto al usuario. ¿Qué elementos aparecen aquí variarán con los contenedores y objetos implicados.

Para construir este combinado **ayuda** menú, la arquitectura de contención de documentos activos modifica el procedimiento normal de documentos OLE. Según los documentos OLE, la barra de menú combinado puede tener seis grupos de menús, es decir, **archivo**, **editar**, **contenedor**, **objeto**,  **Ventana**, **ayuda**, en ese orden. En cada grupo, puede haber cero o más menús. Los grupos de **archivo**, **contenedor**, y **ventana** pertenece al contenedor y los grupos de **editar**, **(objeto),** y **ayuda** pertenecen al objeto. Cuando el objeto que desea realizar la combinación de menús, crea una barra de menús en blanco y lo pasa al contenedor. El contenedor, a continuación, inserta sus menús, mediante una llamada a `IOleInPlaceFrame::InsertMenus`. El objeto también pasa una estructura que es una matriz de seis valores LARGOS (**OLEMENUGROUPWIDTHS**). Después de insertar los menús, el contenedor marca cuántos menús agregó a cada uno de sus grupos y, a continuación, se devuelve. A continuación, el objeto inserta sus menús, prestando atención al recuento de los menús en cada grupo de contenedores. Por último, el objeto pasa la barra de menú combinado y la matriz (que contiene el recuento de los menús de cada grupo) a OLE, que devuelve un opaco "descriptor de menú" controlar. Más adelante el objeto pasa el identificador y la barra de menú combinado en el contenedor, a través de `IOleInPlaceFrame::SetMenu`. En este momento, el contenedor muestra la barra de menú combinado y también pasa el identificador a OLE, para que pueda realizar OLE correcto envío de mensajes de menú.

En el procedimiento de documento activo modificado, el objeto debe inicializar primero el **OLEMENUGROUPWIDTHS** elementos a cero antes de pasarlos al contenedor. El contenedor realiza una inserción de menú normal con una excepción: las inserciones de contenedor un **ayuda** menú como el último elemento y almacena el valor 1 en la última entrada (sexta) de la **OLEMENUGROUPWIDTHS** matriz (es decir, width [5], que pertenece al grupo de Ayuda del objeto). Esto **ayuda** menú tendrá solo un elemento que es un submenú, el "**ayuda contenedor** >" menú en cascada como se describió anteriormente.

El objeto, a continuación, ejecuta su código de inserción de menú normal, excepto que antes de insertar su **ayuda** menú, comprueba la sexta entrada de la **OLEMENUGROUPWIDTHS** matriz. Si el valor es 1 y el nombre del último menú es **ayuda** (o la cadena localizada), a continuación, inserta el objeto su **ayuda** menú como submenú del contenedor de la **ayuda** menú.

El objeto, a continuación, Establece el sexto elemento de **OLEMENUGROUPWIDTHS** a cero y se incrementa en uno el quinto elemento. Esto permite a OLE saber que el **ayuda** menú pertenece al contenedor y se deberían enrutar los mensajes de menú correspondiente a ese menú (y sus submenús) en el contenedor. A continuación, es responsabilidad del contenedor para reenviar **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**y otros mensajes relacionados con el menú que pertenecen a los objetos parte de la **ayuda** menú. Esto se logra mediante el uso de **WM_INITMENU** para borrar una marca que indica al contenedor si el usuario haya navegado en el objeto **ayuda** menú. El contenedor inspecciona **WM_MENUSELECT** para entrada o salida de cualquier elemento en el **ayuda** menú que no haya agregado el contenedor. En la entrada, significa que el usuario haya navegado a un menú de objetos, por lo que el contenedor establece la marca "en el menú de Ayuda del objeto" y el estado de dicha marca utiliza para reenviar cualquier **WM_MENUSELECT**, **WM_INITMENUPOPUP**y  **WM_COMMAND** mensajes, como mínimo, en la ventana de objetos. (En la salida, el contenedor borra la marca y, a continuación, procesa estos mismos mensajes de sí mismo). El contenedor debe utilizar la ventana devuelta desde el objeto `IOleInPlaceActiveObejct::GetWindow` funcionar como el destino para estos mensajes.

Si el objeto detecta un cero en el sexto elemento de **OLEMENUGROUPWIDTHS**, continúa de acuerdo con las reglas normales de documentos OLE. Este procedimiento trata los contenedores que participan en **ayuda** combinación, así como aquellos que no lo hacen de menús.

Cuando el objeto llama `IOleInPlaceFrame::SetMenu`, antes de mostrar el menú combinado de la barra, las comprobaciones de contenedor si el **ayuda** menú tiene un submenú adicional, además de lo que se ha insertado el contenedor. Si es así, el contenedor deja su **ayuda** menú en la barra de menú combinado. Si el **ayuda** menú no tiene un submenú adicional, el contenedor se quitará su **ayuda** menú en la barra de menú combinado. Este procedimiento trata los objetos que participan en **ayuda** combinación, así como aquellos que no lo hacen de menús.

Por último, cuando sea el momento para desensamblar el menú, el objeto quita insertada **ayuda** menú además de quitar la otra inserta los menús. Cuando el contenedor quita sus menús, quitará su **ayuda** menú además de los otros menús que se han insertado.

## <a name="see-also"></a>Vea también

[Contenedores de documentos activos](../mfc/active-document-containers.md)

