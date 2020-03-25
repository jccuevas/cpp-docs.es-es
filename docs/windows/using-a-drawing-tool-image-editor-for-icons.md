---
title: 'Cómo: usar una herramienta de dibujo'
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
ms.openlocfilehash: 61c06ee3fecac18fb95663c0d13474b8bd3b94f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214388"
---
# <a name="how-to-use-a-drawing-tool"></a>Cómo: usar una herramienta de dibujo

El **Editor de imágenes** tiene herramientas de dibujo y borrado a mano alzada que funcionan de la misma manera. Seleccione la herramienta y, si es necesario, [Seleccione los colores de primer plano y de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) , y las opciones de tamaño y forma. A continuación, mueva el puntero a la imagen y haga clic o arrastre para dibujar y borrar.

## <a name="drawing-tools"></a>Herramientas de dibujo

Puede seleccionar herramientas de dibujo en la barra de herramientas del **Editor de imágenes** o en el menú **imagen** . Al seleccionar la herramienta de **borrador** , la herramienta **pincel** o la herramienta **aerógrafo** , el selector de opciones muestra las opciones de la herramienta.

> [!TIP]
>  La información sobre herramientas aparece cuando se mantiene el cursor sobre los botones de la [barra de herramientas del editor de imágenes](../windows/toolbar-image-editor-for-icons.md). Estas sugerencias le ayudarán a identificar los botones específicos que se mencionan aquí.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Para seleccionar y usar una herramienta de dibujo desde la barra de herramientas del editor de imágenes

1. Seleccione un botón en la barra de herramientas del **Editor de imágenes** .

   - La herramienta de **borrador** pinta sobre la imagen con el color de fondo actual al presionar el botón primario del mouse.

      > [!TIP]
      > En lugar de usar la herramienta de **borrador** , puede que le resulte más cómodo dibujar en el color de fondo con una de las herramientas de dibujo.

   - La herramienta **lápiz** dibuja FreeHand en un ancho constante de un píxel.

   - La herramienta **pincel** tiene varias formas y tamaños.

   - La herramienta **aerógrafo** distribuye aleatoriamente los píxeles de color alrededor del centro del pincel.

1. Si es necesario, seleccione colores y un pincel:

   - En la [paleta de colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

   - En el [selector de opciones](../windows/toolbar-image-editor-for-icons.md), seleccione una forma que represente el pincel que desee usar.

1. Señale a la posición de la imagen en la que desea empezar a dibujar o pintar. El puntero cambia de forma según la herramienta seleccionada.

1. Presione el botón primario del mouse (para el color de primer plano) o el botón secundario del mouse (para el color de fondo) y manténgalo presionado mientras dibuja.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Para seleccionar y usar una herramienta de dibujo desde el menú imagen

1. Vaya a la **imagen** de menú > **herramientas**.

1. En el submenú en cascada, elija la herramienta que desea usar.

## <a name="lines-or-closed-figures"></a>Líneas o figuras cerradas

Las herramientas del **Editor de imágenes** para dibujar líneas y figuras cerradas funcionan de la misma manera: Coloque el punto de inserción en un punto y arrástrelo a otro. En el caso de las líneas, estos puntos son los extremos. En el caso de las figuras cerradas, estos puntos son esquinas opuestas de un rectángulo que delimita la figura.

Las líneas se dibujan en un ancho determinado por la selección de pincel actual y las figuras con fotogramas se dibujan en un ancho determinado por la selección de ancho actual. Las líneas y todas las figuras, tanto las tramas como las rellenadas, se dibujan en el color de primer plano actual si se presiona el botón primario del mouse o en el color de fondo actual si se presiona el botón secundario del mouse.

### <a name="to-draw-a-line"></a>Para dibujar una línea

1. Use la [barra de herramientas del editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o vaya a la **imagen** de menú> **herramientas** y elija la herramienta **línea** .

1. Si es necesario, seleccione colores y un pincel:

   - En la [paleta de colores](../windows/colors-window-image-editor-for-icons.md), seleccione el botón primario del mouse para seleccionar un color de primer plano o el botón secundario del mouse para seleccionar un color de fondo.

   - En el [selector de opciones](../windows/toolbar-image-editor-for-icons.md), seleccione una forma que represente el pincel que desee usar.

1. Coloque el puntero en el punto inicial de la línea.

1. Arrastre hasta el punto de conexión de la línea.

### <a name="to-draw-a-closed-figure"></a>Para dibujar una figura cerrada

1. Use la barra de herramientas del **Editor de imágenes** o vaya a la **imagen** de menú > **herramientas** y seleccione una herramienta **de dibujo de figuras cerradas** .

   Las herramientas de **dibujo de imagen cerrada** crean figuras como se indica en sus respectivos botones.

1. Si es necesario, seleccione los colores y el ancho de línea.

1. Mueva el puntero a una esquina del área rectangular en la que desea dibujar la figura.

1. Arrastre el puntero a la esquina opuesta diagonalmente.

## <a name="custom-brushes"></a>Pinceles personalizados

Un pincel personalizado es una parte rectangular de una imagen que se selecciona y se usa como uno de los pinceles predefinidos del **Editor de imágenes**. Todas las operaciones que se pueden realizar en una selección se pueden realizar también en un pincel personalizado.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Para crear un pincel personalizado a partir de una parte de una imagen

1. Seleccione la parte de la imagen que desea usar para un pincel.

1. Mantenga presionada la tecla **MAYÚS** , elija en la selección y arrástrela a través de la imagen, o bien vaya a **imagen** de menú > **usar selección como pincel**.

   La selección se convierte en un pincel personalizado que distribuye los colores de la selección a través de la imagen. Las copias de la selección se quedan a lo largo del trazado de arrastre. Cuanto más lentamente arrastre, más copias se realizarán.

   > [!NOTE]
   > Al seleccionar la **opción usar una selección como pincel** sin seleccionar primero una parte de la imagen, se usará toda la imagen como pincel. El resultado de utilizar un pincel personalizado también dependerá de si ha seleccionado un [fondo opaco o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Los píxeles de un pincel personalizado que coinciden con el color de fondo actual suelen ser transparentes: no dibujan sobre la imagen existente. Puede cambiar este comportamiento para que los píxeles del color de fondo pinten sobre la imagen existente.

Puede usar el pincel personalizado como una marca o una galería de símbolos para crear distintos efectos especiales.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Para dibujar formas de pincel personalizadas en el color de fondo

1. Seleccione un fondo opaco o transparente.

1. Establezca el color de fondo en el color en el que desea dibujar.

1. Coloque el pincel personalizado en el que desea dibujar.

1. Seleccione el botón secundario del mouse. Las regiones opacas del pincel personalizado se dibujan en el color de fondo.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Para doblar o dividir el tamaño del pincel personalizado

Presione la tecla signo **más** ( **+** ) para doblar el tamaño del pincel o la tecla signo **menos** ( **-** ) para dividirla.

### <a name="to-cancel-the-custom-brush"></a>Para cancelar el pincel personalizado

Presione **ESC** o elija otra herramienta de dibujo.

## <a name="requirements"></a>Requisitos

None

## <a name="see-also"></a>Consulte también

[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)<br/>
[Cómo: crear un icono u otra imagen](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Cómo: editar una imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Cómo: trabajar con colores](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
