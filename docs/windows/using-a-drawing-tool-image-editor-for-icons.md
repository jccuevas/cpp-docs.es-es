---
title: 'Cómo: Usar una herramienta de dibujo'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359850"
---
# <a name="how-to-use-a-drawing-tool"></a>Cómo: Usar una herramienta de dibujo

El **Editor de imágenes** tiene herramientas de dibujo y borrado a mano alzada que funcionan de la misma manera. Seleccione la herramienta y, si es necesario, [seleccione los colores](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) de primer plano y de fondo y las opciones de tamaño y forma. A continuación, mueva el puntero a la imagen y haga clic o arrastre para dibujar y borrar.

## <a name="drawing-tools"></a>Herramientas de dibujo

Puede seleccionar herramientas de dibujo en la barra de herramientas Editor de **imágenes** o en el menú **Imagen.** Al seleccionar la herramienta **Borrador,** la herramienta **Pincel** o la herramienta **Aerógrafo,** el selector de opciones muestra las opciones de esa herramienta.

> [!TIP]
> Las sugerencias de herramientas aparecen al colocar el cursor sobre los botones de la barra de herramientas del [Editor](../windows/toolbar-image-editor-for-icons.md)de imágenes . Estos consejos le ayudarán a identificar los botones específicos mencionados aquí.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Para seleccionar y utilizar una herramienta de dibujo en la barra de herramientas editor de imágenes

1. Seleccione un botón en la barra de herramientas **Editor de imágenes.**

   - La herramienta **Borrador** pinta sobre la imagen con el color de fondo actual al pulsar el botón izquierdo del ratón.

      > [!TIP]
      > En lugar de utilizar la herramienta **Borrador,** puede resultar más conveniente dibujar en el color de fondo con una de las herramientas de dibujo.

   - La herramienta **Lápiz** dibuja a mano alzada en un ancho constante de un píxel.

   - La herramienta **Pincel** tiene varias formas y tamaños.

   - La herramienta **Aerógrafo** distribuye aleatoriamente los píxeles de color alrededor del centro del pincel.

1. Si es necesario, seleccione colores y un pincel:

   - En la [paleta Colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón izquierdo del ratón para seleccionar un color de primer plano o el botón derecho del ratón para seleccionar un color de fondo.

   - En el [selector Opciones](../windows/toolbar-image-editor-for-icons.md), seleccione una forma que represente el pincel que desea utilizar.

1. Señale el lugar de la imagen donde desea empezar a dibujar o pintar. El puntero cambia de forma según la herramienta seleccionada.

1. Pulse el botón izquierdo del ratón (para el color de primer plano) o el botón derecho del ratón (para el color de fondo) y mantenlo pulsado mientras dibuja.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Para seleccionar y utilizar una herramienta de dibujo en el menú Imagen

1. Vaya al menú**Herramientas** **de imagen** > .

1. En el submenú en cascada, elija la herramienta que desea utilizar.

## <a name="lines-or-closed-figures"></a>Líneas o figuras cerradas

Las herramientas del **Editor** de imágenes para dibujar líneas y figuras cerradas funcionan de la misma manera: se coloca el punto de inserción en un punto y se arrastra a otro. Para las líneas, estos puntos son los puntos finales. Para las figuras cerradas, estos puntos son esquinas opuestas de un rectángulo que delimita la figura.

Las líneas se dibujan en un ancho determinado por la selección actual del pincel y las figuras enmarcadas se dibujan en un ancho determinado por la selección de anchura actual. Las líneas y todas las figuras, tanto enmarcadas como rellenadas, se dibujan en el color de primer plano actual si pulsa el botón izquierdo del ratón o en el color de fondo actual si pulsa el botón derecho del ratón.

### <a name="to-draw-a-line"></a>Para dibujar una línea

1. Utilice la barra de herramientas Editor de [imágenes](../windows/toolbar-image-editor-for-icons.md) o vaya al **menú**> **Herramientas** de imagen y elija la herramienta **Línea.**

1. Si es necesario, seleccione colores y un pincel:

   - En la [paleta Colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón izquierdo del ratón para seleccionar un color de primer plano o el botón derecho del ratón para seleccionar un color de fondo.

   - En el [selector Opciones](../windows/toolbar-image-editor-for-icons.md), seleccione una forma que represente el pincel que desea utilizar.

1. Coloque el puntero en el punto inicial de la línea.

1. Arrastre hasta el punto final de la línea.

### <a name="to-draw-a-closed-figure"></a>Para dibujar una figura cerrada

1. Utilice la barra de herramientas Editor de **imágenes** o vaya al **menú** > **Herramientas** de imagen y seleccione una herramienta Dibujo de **figura cerrada.**

   Las herramientas **Dibujo de figura cerrada** crean figuras como se indica en sus respectivos botones.

1. Si es necesario, seleccione colores y un ancho de línea.

1. Mueva el puntero a una esquina del área rectangular en la que desea dibujar la figura.

1. Arrastre el puntero a la esquina diagonalmente opuesta.

## <a name="custom-brushes"></a>Pinceles personalizados

Un pincel personalizado es una parte rectangular de una imagen que se recoge y se utiliza como uno de los pinceles ya hechos del **Editor**de imágenes. Todas las operaciones que puede realizar en una selección, también se puede realizar en un pincel personalizado.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Para crear un pincel personalizado a partir de una parte de una imagen

1. Seleccione la parte de la imagen que desea utilizar para un pincel.

1. Mantenga pulsada la tecla **Mayús,** elija en la selección y arrástrela a través de la imagen, o vaya al **menú** > **Selección de uso**de imagen como pincel .

   La selección se convierte en un pincel personalizado que distribuye los colores de la selección a través de la imagen. Las copias de la selección se dejan a lo largo del trazado de arrastre. Cuanto más lentamente arrastres, más copias se hacen.

   > [!NOTE]
   > Al seleccionar **Usar una selección como pincel** sin seleccionar primero una parte de la imagen, se utilizará toda la imagen como pincel. El resultado del uso de un pincel personalizado también dependerá de si ha seleccionado un [fondo opaco o transparente.](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

Los píxeles de un pincel personalizado que coinciden con el color de fondo actual son normalmente transparentes: no pintan sobre la imagen existente. Puede cambiar este comportamiento para que los píxeles de color de fondo pinten sobre la imagen existente.

Puede utilizar el pincel personalizado como un sello o una galería de símbolos para crear diferentes efectos especiales.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Para dibujar formas de pincel personalizadas en el color de fondo

1. Seleccione un fondo opaco o transparente.

1. Establezca el color de fondo en el color en el que desea dibujar.

1. Coloque el pincel personalizado donde desee dibujar.

1. Seleccione el botón derecho del ratón. Las regiones opacas del pincel personalizado se dibujan en el color de fondo.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Para duplicar o reducir a la mitad el tamaño del pincel personalizado

Presione la tecla**+** Signo **más** ( ) para duplicar**-** el tamaño del pincel, o la tecla Signo **menos** ( ) para reducirlo a la mitad.

### <a name="to-cancel-the-custom-brush"></a>Para cancelar el pincel personalizado

Pulse **Esc** o elija otra herramienta de dibujo.

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: Crear un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: Editar una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Cómo: Trabajar con Color](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Teclas del acelerador](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
