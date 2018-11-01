---
title: Usar una herramienta de dibujo (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: de6308ad396a9f9e355ecefdecca444c551d51f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677089"
---
# <a name="using-a-drawing-tool-image-editor-for-icons"></a>Usar una herramienta de dibujo (Editor de imágenes para iconos)

El **imagen** editor a mano alzado del dibujo y el borrado de las herramientas de todo el trabajo de la misma manera: seleccione la herramienta y, si es necesario, [seleccionar los colores de primer plano y fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) y opciones de tamaño y forma. A continuación, mueva el puntero a la imagen y haga clic o arrastre para dibujar y borrar.

Cuando se selecciona el **borrador** herramienta, **pincel** herramienta, o **aerógrafo** herramienta, el selector de opciones muestra las opciones de la herramienta.

> [!TIP]
> En lugar de usar el **borrador** herramienta, le resultará más cómodo dibujar en el color de fondo con una de las herramientas de dibujo.

Puede seleccionar las herramientas de dibujo desde el **Editor de imágenes** barra de herramientas o el **imagen** menú.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Para seleccionar y usar una herramienta de dibujo de la barra de herramientas del Editor de imágenes

1. Haga clic en un botón en el **Editor de imágenes** barra de herramientas.

   - El **borrador** herramienta pinta la imagen con el color de fondo actual cuando se presiona el botón primario del mouse.

   - El **lápiz** herramienta dibuja a mano alzada con un ancho constante de un píxel.

   - El **selector de opciones determina la forma y el tamaño de la herramienta pincel**.

   - El **aerógrafo** herramienta distribuye aleatoriamente los píxeles de color en torno al centro del pincel.

        > [!TIP]
        >  Información sobre herramientas aparece cuando desplace el cursor sobre los botones en la [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md). Estas sugerencias le ayudarán a identificar los botones que se mencionan aquí.

2. Si es necesario, seleccione los colores y un pincel:

   - En el [paleta de colores](../windows/colors-window-image-editor-for-icons.md), haga clic en el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

   - En el [Selector de opciones](../windows/toolbar-image-editor-for-icons.md), haga clic en una forma que representa el pincel que desea usar.

3. Elija el lugar en la imagen donde desee empezar a dibujar o pintar. El puntero cambia de forma según la herramienta seleccionada.

4. Presione el botón primario del mouse (para el color de primer plano) o el botón secundario del mouse (para el color de fondo) y manténgalo presionado mientras dibuja.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Para seleccionar y usar una herramienta de dibujo en el menú imagen

1. Haga clic en el **imagen** menú y seleccione el **herramientas** comando.

2. En el submenú en cascada, elija la herramienta que desea usar.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)