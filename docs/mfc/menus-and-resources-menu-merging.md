---
title: 'Menús y recursos: Combinación de menús'
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 03d27443f90634b5d787eee25acc951d24178f42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626221"
---
# <a name="menus-and-resources-menu-merging"></a>Menús y recursos: Combinación de menús

En este artículo se detallan los pasos necesarios para que las aplicaciones de documentos OLE controlen correctamente la edición y la activación en contexto. La activación en contexto supone un desafío para las aplicaciones de contenedor y servidor (componente). El usuario permanece en la misma ventana de marco (en el contexto del documento contenedor), pero en realidad ejecuta otra aplicación (el servidor). Esto requiere la coordinación entre los recursos de las aplicaciones de contenedor y de servidor.

Los temas que se tratan en este artículo son:

- [Diseños de menú](#_core_menu_layouts)

- [Barras de herramientas y barras de estado](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Diseños de menú

El primer paso es coordinar los diseños del menú. Las aplicaciones de contenedor deben crear un nuevo menú que se usará solo cuando se activen los elementos incrustados en su lugar. Como mínimo, este menú debe constar de lo siguiente, en el orden mostrado:

1. Menú Archivo idéntico al utilizado cuando los archivos están abiertos. (Normalmente no se coloca ningún otro elemento de menú delante del siguiente elemento).

1. Dos separadores consecutivos.

1. Menú ventana idéntico al utilizado cuando los archivos están abiertos (solo si la aplicación contenedora en una aplicación MDI). Algunas aplicaciones pueden tener otros menús, como un menú de opciones, que pertenecen a este grupo, que permanece en el menú cuando se activa un elemento incrustado en su lugar.

    > [!NOTE]
    >  Puede haber otros menús que afecten a la vista del documento contenedor, como el zoom. Estos menús contenedores aparecen entre los dos separadores de este recurso de menú.

Las aplicaciones de servidor (componente) también deben crear un nuevo menú específicamente para la activación en contexto. Debe ser como el menú que se usa cuando los archivos están abiertos, pero sin elementos de menú, como archivos y ventanas que manipulan el documento del servidor en lugar de los datos. Normalmente, este menú consta de lo siguiente:

1. Menú Edición idéntico al que se usa cuando los archivos están abiertos.

1. Separador.

1. Menús de edición de objetos, como el menú de lápiz en la aplicación de ejemplo Scribble.

1. Separador.

1. Menú ayuda.

Para ver un ejemplo, consulte el diseño de algunos menús en contexto de ejemplo para un contenedor y un servidor. Los detalles de cada elemento de menú se han quitado para que el ejemplo sea más claro. El menú en contexto del contenedor tiene las siguientes entradas:

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

Los separadores consecutivos indican dónde debe ir la primera parte del menú del servidor. Ahora mire el menú en contexto del servidor:

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

Los separadores aquí indican dónde debería ir el segundo grupo de elementos de menú contenedor. La estructura de menú resultante cuando un objeto de este servidor se activa en su lugar dentro de este contenedor tiene el siguiente aspecto:

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

Como puede ver, los separadores se han reemplazado por los grupos diferentes del menú de cada aplicación.

La aplicación de servidor también debe proporcionar las tablas de aceleradores asociadas al menú en contexto. El contenedor los incorporará en sus propias tablas de aceleradores.

Cuando se activa un elemento incrustado en contexto, el marco de trabajo carga el menú en contexto. A continuación, pide a la aplicación de servidor su menú para la activación en contexto y lo inserta donde están los separadores. Así es como se combinan los menús. Los menús se obtienen del contenedor para que funcionen en el archivo y la ubicación de la ventana, y se obtienen los menús del servidor para que funcionen en el elemento.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Barras de herramientas y barras de estado

Las aplicaciones de servidor deben crear una nueva barra de herramientas y almacenar su mapa de bits en un archivo independiente. Las aplicaciones generadas por el Asistente para aplicaciones almacenan este mapa de bits en un archivo denominado ITOOLBAR. BMP. La nueva barra de herramientas reemplaza la barra de herramientas de la aplicación contenedora cuando el elemento del servidor está activado en contexto y debe contener los mismos elementos que la barra de herramientas normal, pero quita los iconos que representan los elementos de los menús archivo y ventana.

Esta barra de herramientas se carga en la `COleIPFrameWnd` clase derivada de, creada por el Asistente para aplicaciones. La aplicación contenedora controla la barra de estado. Para obtener más información sobre la implementación de ventanas de marco en contexto, consulte [servidores: implementar un servidor](servers-implementing-a-server.md).

## <a name="see-also"></a>Consulte también

[Menús y recursos (OLE)](menus-and-resources-ole.md)<br/>
[Activación](activation-cpp.md)<br/>
[Servidores](servers.md)<br/>
[Contenedores](containers.md)
