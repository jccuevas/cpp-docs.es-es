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
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364770"
---
# <a name="menus-and-resources-menu-merging"></a>Menús y recursos: Combinación de menús

En este artículo se detallan los pasos necesarios para que las aplicaciones de documentos OLE controlen correctamente la edición visual y la activación in situ. La activación en contexto supone un desafío tanto para las aplicaciones de contenedor como de servidor (componente). El usuario permanece en la misma ventana de marco (dentro del contexto del documento contenedor) pero en realidad está ejecutando otra aplicación (el servidor). Esto requiere coordinación entre los recursos del contenedor y las aplicaciones de servidor.

Los temas tratados en este artículo incluyen:

- [Diseños de menú](#_core_menu_layouts)

- [Barras de herramientas y barras de estado](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Diseños de menú

El primer paso es coordinar los diseños de menú. Las aplicaciones contenedoras deben crear un nuevo menú que solo se usará cuando los elementos incrustados se activen en su lugar. Como mínimo, este menú debe consistir en lo siguiente, en el orden indicado:

1. Menú de archivos idéntico al utilizado cuando los archivos están abiertos. (Por lo general, no se colocan otros elementos de menú antes del siguiente elemento.)

1. Dos separadores consecutivos.

1. Menú de ventana idéntico al utilizado cuando los archivos están abiertos (solo si la aplicación contenedora en una aplicación MDI). Algunas aplicaciones pueden tener otros menús, como un menú Opciones, que pertenecen a este grupo, que permanece en el menú cuando se activa un elemento incrustado en su lugar.

    > [!NOTE]
    >  Puede haber otros menús que afecten a la vista del documento contenedor, como Zoom. Estos menús contenedor aparecen entre los dos separadores de este recurso de menú.

Las aplicaciones de servidor (componente) también deben crear un nuevo menú específicamente para la activación in situ. Debe ser como el menú utilizado cuando los archivos están abiertos, pero sin elementos de menú, como Archivo y Ventana que manipulan el documento del servidor en lugar de los datos. Normalmente, este menú consta de lo siguiente:

1. Editar menú idéntico al utilizado cuando los archivos están abiertos.

1. Separador.

1. Menús de edición de objetos, como el menú Pluma de la aplicación de ejemplo Scribble.

1. Separador.

1. Menú de ayuda.

Por ejemplo, mire el diseño de algunos menús in situ de ejemplo para un contenedor y un servidor. Los detalles de cada elemento de menú se han eliminado para que el ejemplo sea más claro. El menú in situ del contenedor tiene las siguientes entradas:

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

Los separadores consecutivos indican dónde debe ir la primera parte del menú del servidor. Ahora mire el menú in situ del servidor:

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

Los separadores aquí indican dónde debe ir el segundo grupo de elementos de menú contenedor. La estructura de menú resultante cuando un objeto de este servidor se activa en su lugar dentro de este contenedor tiene este aspecto:

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

Como puede ver, los separadores se han reemplazado por los diferentes grupos del menú de cada aplicación.

La aplicación de servidor también debe proporcionar tablas aceleradoras asociadas al menú in situ. El contenedor los incorporará en sus propias mesas aceleradoras.

Cuando un elemento incrustado se activa en su lugar, el marco de trabajo carga el menú in situ. A continuación, solicita a la aplicación de servidor su menú para la activación en contexto y lo inserta donde están los separadores. Así se combinan los menús. Obtiene menús del contenedor para operar en la ubicación de archivos y ventanas, y obtendrá menús del servidor para operar en el elemento.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Barras de herramientas y barras de estado

Las aplicaciones de servidor deben crear una nueva barra de herramientas y almacenar su mapa de bits en un archivo independiente. Las aplicaciones generadas por el asistente de aplicaciones almacenan este mapa de bits en un archivo denominado ITOOLBAR. Bmp. La nueva barra de herramientas reemplaza la barra de herramientas de la aplicación contenedora cuando el elemento del servidor se activa en su lugar y debe contener los mismos elementos que la barra de herramientas normal, pero quitar los iconos que representan elementos en los menús Archivo y Ventana.

Esta barra de `COleIPFrameWnd`herramientas se carga en la clase derivada, creada automáticamente por el asistente de aplicación. La aplicación contenedora controla la barra de estado. Para obtener más información sobre la implementación de ventanas de marco in situ, vea [Servidores: implementar un servidor](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Consulte también

[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Activación](../mfc/activation-cpp.md)<br/>
[Servidores](../mfc/servers.md)<br/>
[Contenedores](../mfc/containers.md)
