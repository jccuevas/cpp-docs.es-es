---
title: Dibujar líneas o figuras cerradas (Editor de imágenes para iconos)
ms.date: 11/04/2016
helpviewer_keywords:
- Image editor [C++], drawing lines
- shapes, drawing
ms.assetid: 7edd86db-77b1-451f-8001-bbfed9c6304f
ms.openlocfilehash: a33376529faadd2433f704505aa0be8d4cc03033
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449080"
---
# <a name="drawing-lines-or-closed-figures-image-editor-for-icons"></a>Dibujar líneas o figuras cerradas (Editor de imágenes para iconos)

El editor de imágenes de las herramientas de dibujo de líneas y figuras cerradas todas funcionan de la misma manera: sitúe el cursor en un punto y arrastrar a otra. Para las líneas, estos puntos son los puntos de conexión. Figuras cerradas, estos puntos son las esquinas opuestas de un rectángulo delimitador en la ilustración.

Las líneas se dibujan con un ancho determinado por la selección de pincel actual y las figuras enmarcadas se dibujan con un ancho determinado por la selección actual del ancho. Líneas y las figuras, enmarcado tanto rellenado, se dibujan en el color de primer plano actual si presiona el botón primario del mouse, o en el color de fondo actual, si presiona el botón secundario del mouse.

### <a name="to-draw-a-line"></a>Para dibujar una línea

1. En el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) (o desde el **imagen** menú, **herramientas** comando), haga clic en el **línea** herramienta.

2. Si es necesario, seleccione los colores y un pincel:

   - En el [paleta de colores](../windows/colors-window-image-editor-for-icons.md), haga clic en el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

   - En el [selector de opciones](../windows/toolbar-image-editor-for-icons.md), haga clic en una forma que representa el pincel que desea usar.

3. Coloque el puntero en el punto de partida de la línea.

4. Arrastre al extremo de la línea.

### <a name="to-draw-a-closed-figure"></a>Para dibujar una figura cerrada.

1. En el **Editor de imágenes** barra de herramientas (o desde el **imagen** menú, **herramientas** comando), haga clic en un **dibujo de figuras cerradas** herramienta.

   El **dibujo de figuras cerradas** herramientas crean figuras a como se indica en sus respectivos botones.

2. Si es necesario, seleccione los colores y un ancho de línea.

3. Mueva el puntero a una de las esquinas del área rectangular en la que va a dibujar en la ilustración.

4. Arrastre el puntero a la esquina diagonalmente opuesta.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)