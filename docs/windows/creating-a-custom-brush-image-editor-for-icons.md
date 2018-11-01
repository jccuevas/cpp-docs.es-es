---
title: Crear un pincel personalizado (Editor de imágenes para iconos)
ms.date: 11/04/2016
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
ms.openlocfilehash: 01d5badc70aac3e51a8731c5ea62b30a27d2962a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502861"
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>Crear un pincel personalizado (Editor de imágenes para iconos)

Un pincel personalizado es una parte rectangular de una imagen que recoger y usar como uno de los **imagen** pincel predefinido del editor. Todas las operaciones que puede realizar en una selección, puede realizar en un pincel personalizado también.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Para crear un pincel personalizado desde una parte de una imagen

1. [Seleccione la parte de la imagen](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) que desea usar para un pincel.

2. Que contiene el **MAYÚS** tecla presionada, haga clic en la selección y arrastre el puntero sobre la imagen.

   \- o -

3. Desde el **imagen** menú, elija **usar la selección como pincel**.

   La selección se convierte en un pincel personalizado que distribuye los colores de la selección en la imagen. Copias de la selección se dejan a lo largo de la trayectoria de arrastre. Cuanto más lentamente arrastre, se realizan las copias más.

   > [!NOTE]
   > Al hacer clic en el **utilizar una selección como pincel** sin seleccionar primero una parte de la imagen se utiliza toda la imagen como un pincel. El resultado de usar un pincel personalizado también depende de si ha seleccionado un [fondo transparente u opaco](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Píxeles de un pincel personalizado que coincida con el color de fondo actual normalmente son transparentes: no pintan la imagen existente. Puede cambiar este comportamiento para que se pinte píxeles de color de fondo a través de la imagen existente.

Puede usar el pincel personalizado como un sello o una galería de símbolos para crear una variedad de efectos especiales.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Para dibujar formas de pincel personalizado en el color de fondo

1. [Seleccionar un fondo opaco o transparente](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

2. [Establecer el color de fondo](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) al color en el que va a dibujar.

3. Coloque el pincel personalizado donde va a dibujar.

4. Haga clic en el botón secundario del mouse. Las regiones opacas del pincel personalizado se dibujan en el color de fondo.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Para duplicar o a la mitad del tamaño del pincel personalizado

1. Presione el **signo** (**+**) clave duplicar el tamaño del pincel, o el **signo** (**-**) para dividirlo .

### <a name="to-cancel-the-custom-brush"></a>Para cancelar el pincel personalizado

1. Presione **Esc** o elija otra herramienta de dibujo.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)