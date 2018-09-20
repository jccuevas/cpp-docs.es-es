---
title: 'Menús y recursos: combinación de menús | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f4e76902335477ba507e6f3e7a66c5f862b8543
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418676"
---
# <a name="menus-and-resources-menu-merging"></a>Menús y recursos: Combinación de menús

En este artículo se detalla los pasos necesarios para las aplicaciones de documento OLE controlar la edición visual y la activación en contexto correctamente. Activación en contexto supone un desafío para el contenedor y servidor de aplicaciones (componente). El usuario permanece en la misma ventana de marco (dentro del contexto del documento contenedor), pero está realmente se está ejecutando otra aplicación (el servidor). Esto requiere la coordinación entre los recursos de las aplicaciones de contenedor y servidor.

Los temas tratados en este artículo incluyen:

- [Diseños de menú](#_core_menu_layouts)

- [Las barras de herramientas y barras de estado](#_core_toolbars_and_status_bars)

##  <a name="_core_menu_layouts"></a> Diseños de menú

El primer paso es coordinar diseños de menú. Para obtener más información, consulte el **creación de menús** sección [consideraciones sobre la programación de menú](https://msdn.microsoft.com/library/ms647557.aspx) en el SDK de Windows.

Aplicaciones de contenedor deben crear un nuevo menú para usarse solo cuando se activan los elementos incrustados en su lugar. Como mínimo, este menú debe constar de los siguientes, en el orden mostrado:

1. Menú archivo idéntico al utilizado cuando se abren los archivos. (Normalmente no hay otros elementos de menú se colocan antes del siguiente elemento).

1. Dos separadores consecutivos.

1. Menú Ventana idéntico al utilizado cuando se abren los archivos (solo si la aplicación contenedora en una aplicación MDI). Algunas aplicaciones pueden tener otros menús, como un menú de opciones, que pertenecen a este grupo, que permanece en el menú cuando se activa un elemento incrustado en su lugar.

    > [!NOTE]
    >  Puede haber otros menús que afectan a la vista del documento contenedor, por ejemplo, el Zoom. Estos menús del contenedor aparecen entre los dos separadores de este recurso de menú.

Las aplicaciones de servidor (componente) también deben crear un nuevo menú específicamente para la activación en contexto. Debe ser como el menú que se utiliza cuando los archivos están abiertos, pero sin elementos de menú, como ventana que manipulan el documento del servidor en lugar de los datos y archivos. Normalmente, este menú consta de las siguientes acciones:

1. Editar menú idéntico al utilizado cuando se abren los archivos.

1. Separador.

1. Edición de menús, como el menú de lápiz en la aplicación de ejemplo de Scribble de objetos.

1. Separador.

1. Menú Ayuda.

Para obtener un ejemplo, examine el diseño de algunos menús contextuales de ejemplo para un contenedor y un servidor. Se han quitado los detalles de cada elemento de menú para que el ejemplo más claro. El menú del contenedor de contexto tiene las siguientes entradas:

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

Los separadores consecutivos indican dónde debería ir la primera parte del menú del servidor. Ahora examinemos menús in situ del servidor:

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

Los separadores indican dónde debe ir el segundo grupo de elementos de menú del contenedor. La estructura de menús resultante cuando se activa un objeto de este servidor en contexto dentro de este contenedor tiene este aspecto:

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

Como puede ver, se han reemplazado los separadores con los diferentes grupos de menú de la aplicación.

La aplicación de servidor también deben proporcionar asociadas con el menú en lugar de tablas de aceleradores. El contenedor incorporará a sus propias tablas de aceleradores.

Cuando se activa un elemento incrustado en su lugar, el marco de trabajo carga el menú contextual. A continuación, se pide a la aplicación de servidor para el menú para la activación en contexto y se inserta dónde están los separadores. Se trata de cómo se combinan los menús. Obtener los menús del contenedor para operar en la ubicación del archivo y la ventana, y obtendrá menús desde el servidor para operar en el elemento.

##  <a name="_core_toolbars_and_status_bars"></a> Las barras de herramientas y barras de estado

Las aplicaciones de servidor deben crear una nueva barra de herramientas y almacenar su mapa de bits en un archivo independiente. Las aplicaciones de aplicación generados por el Asistente para almacenan este mapa de bits en un archivo denominado ITOOLBAR. BMP. La nueva barra de herramientas reemplaza la barra de herramientas de la aplicación contenedora cuando el elemento del servidor está activado en su lugar y debe contener los mismos elementos que la barra de herramientas normal, pero quite iconos que representan los elementos en los menús archivo y ventana.

Esta barra de herramientas se carga en su `COleIPFrameWnd`-clase derivada, creada automáticamente el Asistente para aplicaciones. La barra de estado se controla mediante la aplicación contenedora. Para obtener más información sobre la implementación de ventanas de marco en contexto, vea [servidores: implementar un servidor](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Vea también

[Menús y recursos (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Activación](../mfc/activation-cpp.md)<br/>
[Servidores](../mfc/servers.md)<br/>
[Contenedores](../mfc/containers.md)

