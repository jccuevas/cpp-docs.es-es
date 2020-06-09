---
title: Combinar el menú Ayuda
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: 1bd70af6f24ee6f9873b89b2060f4b2d90149c90
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620127"
---
# <a name="help-menu-merging"></a>Combinar el menú Ayuda

Cuando un objeto está activo dentro de un contenedor, el protocolo de combinación de menús de documentos OLE proporciona al objeto un control completo del menú **ayuda** . Como resultado, los temas de ayuda del contenedor no están disponibles a menos que el usuario desactive el objeto. La arquitectura de contención de documentos activos amplía las reglas de la combinación de menús en contexto para permitir tanto el contenedor como un documento activo que está activo para compartir el menú. Las nuevas reglas son simplemente convenciones adicionales sobre qué componente posee qué parte del menú y cómo se construye el menú compartido.

La nueva Convención es sencilla. En los documentos activos, el menú **ayuda** tiene dos elementos de menú de nivel superior organizados de la manera siguiente:

`Help`

`Container Help >`

`Object Help    >`

Por ejemplo, cuando una sección de Word está activa en el enlazador de Office, el menú **ayuda** tendría el siguiente aspecto:

`Help`

`Binder Help >`

`Word Help   >`

Ambos elementos de menú son menús en cascada en los que se proporcionan al usuario los elementos de menú adicionales específicos para el contenedor y el objeto. Los elementos que aparecen aquí variarán con el contenedor y los objetos implicados.

Para construir este menú de **ayuda** combinado, la arquitectura de contención de documentos activos modifica el procedimiento de documentos OLE normal. Según los documentos OLE, la barra de menús combinada puede tener seis grupos de menús, es decir, **archivo**, **edición**, **contenedor**, **objeto**, **ventana**, **ayuda**, en ese orden. En cada grupo, puede haber cero o más menús. El **archivo**, el **contenedor**y la **ventana** de grupos pertenecen al contenedor y los grupos **Editar**, **objeto** y **ayuda** pertenecen al objeto. Cuando el objeto desea realizar la combinación de menús, crea una barra de menús en blanco y la pasa al contenedor. A continuación, el contenedor inserta sus menús mediante una llamada a `IOleInPlaceFrame::InsertMenus` . El objeto también pasa una estructura que es una matriz de seis valores LONG (**OLEMENUGROUPWIDTHS**). Después de insertar los menús, el contenedor marca el número de menús que agregó en cada uno de sus grupos y, a continuación, devuelve. A continuación, el objeto inserta sus menús, preste atención al recuento de menús en cada grupo de contenedores. Por último, el objeto pasa la barra de menús combinada y la matriz (que contiene el recuento de menús de cada grupo) a OLE, que devuelve un identificador de "descriptor de menú" opaco. Posteriormente, el objeto pasa ese identificador y la barra de menús combinada al contenedor, a través de `IOleInPlaceFrame::SetMenu` . En este momento, el contenedor muestra la barra de menús combinada y también pasa el identificador a OLE, de modo que OLE pueda enviar correctamente los mensajes de menú.

En el procedimiento de documento activo modificado, el objeto debe inicializar primero los elementos **OLEMENUGROUPWIDTHS** en cero antes de pasarlos al contenedor. Después, el contenedor realiza una inserción de menú normal con una excepción: el contenedor inserta un menú **ayuda** como el último elemento y almacena un valor de 1 en la última entrada (sexta) de la matriz **OLEMENUGROUPWIDTHS** (es decir, el ancho [5], que pertenece al grupo de ayuda del objeto). Este menú **ayuda** solo tendrá un elemento, que es un submenú, el menú "**ayuda de contenedor** >" en cascada tal y como se ha descrito anteriormente.

Después, el objeto ejecuta su código de inserción de menú normal, excepto que antes de insertar su menú **ayuda** , comprueba la sexta entrada de la matriz **OLEMENUGROUPWIDTHS** . Si el valor es 1 y el nombre del último menú es **ayuda** (o la cadena localizada adecuada), el objeto inserta su menú **ayuda** como submenú del menú **ayuda** del contenedor.

Después, el objeto establece el sexto elemento de **OLEMENUGROUPWIDTHS** en cero e incrementa el quinto elemento en uno. Esto permite a OLE saber que el menú **ayuda** pertenece al contenedor y los mensajes de menú correspondientes a ese menú (y sus submenús) se deben enrutar al contenedor. Después, es responsabilidad del contenedor reenviar **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**y otros mensajes relacionados con el menú que pertenecen a la parte del objeto del menú **ayuda** . Esto se logra mediante el uso de **WM_INITMENU** para borrar una marca que indica al contenedor si el usuario ha navegado en el menú **ayuda** del objeto. A continuación, el contenedor inspecciona **WM_MENUSELECT** para la entrada o salida de cualquier elemento del menú **ayuda** que el contenedor no se agregó a sí mismo. En la entrada, significa que el usuario ha navegado a un menú objeto, por lo que el contenedor establece el marcador "en el menú ayuda de objeto" y usa el estado de esa marca para reenviar los mensajes **WM_MENUSELECT**, **WM_INITMENUPOPUP**y **WM_COMMAND** , como mínimo, a la ventana de objeto. (Al salir, el contenedor borra la marca y, a continuación, procesa estos mismos mensajes). El contenedor debe usar la ventana devuelta desde la función del objeto `IOleInPlaceActiveObejct::GetWindow` como destino de estos mensajes.

Si el objeto detecta un cero en el sexto elemento de **OLEMENUGROUPWIDTHS**, continúa de acuerdo con las reglas normales de documentos OLE. En este procedimiento se describen los contenedores que participan en la combinación del menú **ayuda** , así como los que no lo hacen.

Cuando el objeto llama a `IOleInPlaceFrame::SetMenu` , antes de mostrar la barra de menús combinada, el contenedor comprueba si el menú **ayuda** tiene un submenú adicional, además de lo que el contenedor ha insertado. En ese caso, el contenedor deja su menú **ayuda** en la barra de menús combinada. Si el menú **ayuda** no tiene un submenú adicional, el contenedor quitará su menú **ayuda** de la barra de menús combinada. En este procedimiento se describen los objetos que participan en la combinación del menú **ayuda** y los que no lo hacen.

Por último, cuando es hora de desensamblar el menú, el objeto quita el menú de **ayuda** insertado además de quitar los demás menús insertados. Cuando el contenedor quita sus menús, quita su menú **ayuda** además de los demás menús que ha insertado.

## <a name="see-also"></a>Consulte también

[Contenedores de documentos activos](active-document-containers.md)
