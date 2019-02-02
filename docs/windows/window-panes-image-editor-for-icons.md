---
title: Paneles de la ventana (Editor de imágenes para iconos)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560314"
---
# <a name="window-panes-image-editor-for-icons"></a>Paneles de la ventana (Editor de imágenes para iconos)

El **Editor de imágenes** ventana muestra una imagen de normalmente en dos paneles separados por una barra divisora. Una vista es el tamaño real y la otra se amplía (el factor de ampliación predeterminado es 6). Las vistas de estos dos paneles se actualizan automáticamente: los cambios realizados en un panel se muestran inmediatamente en el otro. Los dos paneles facilitan el trabajo en la vista ampliada de la imagen, en el que pueda distinguir los píxeles individuales y, al mismo tiempo, observar el efecto del trabajo en la vista de tamaño real de la imagen.

Utiliza el espacio se necesita el panel izquierdo (la mitad de la **imagen** ventana) para mostrar la vista de ampliación 1:1 (valor predeterminado) de la imagen. El panel derecho muestra la imagen ampliada (ampliación 6:1 de forma predeterminada). Puede cambiar la ampliación de cada panel utilizando el **Magnify** herramienta en el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md) o mediante las teclas de aceleración.

Puede ampliar el panel menor de la **Editor de imágenes** ventana y usar los dos paneles para mostrar diferentes regiones de una imagen grande. Seleccione esta opción dentro del panel para elegirlo.

Puede cambiar el tamaño relativo de los paneles colocando el puntero en la barra de división y al mover la barra de división hacia la izquierda o derecha. Si desea trabajar en un solo panel, puede mover la barra de división a ambos lados.

Si el **Editor de imágenes** panel es ampliada por un factor de 4 o mayor, puede mostrar una cuadrícula de píxeles que delimita los píxeles individuales de la imagen.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-change-the-magnification-factor"></a>Para cambiar el factor de ampliación

De forma predeterminada, el **imagen** editor muestra la vista en el panel izquierdo al tamaño real y la vista en el panel derecho a las 6 veces el tamaño real. El factor de ampliación (que se muestra en la barra de estado en la parte inferior del área de trabajo) es la relación entre el tamaño real de la imagen y el tamaño de muestra. El factor de forma predeterminada es 6 y el intervalo es de 1 a 10.

1. Seleccione el **Editor de imágenes** panel cuyo factor de ampliación que desee cambiar.

1. En el [barra de herramientas del Editor de imágenes](../windows/toolbar-image-editor-for-icons.md), seleccione la flecha situada a la derecha de la [herramienta aumentar](../windows/toolbar-image-editor-for-icons.md) y seleccione el factor de ampliación desde el submenú: **1 X**, **2 X**, **6 X**, o **8 X**.

   > [!NOTE]
   > Para seleccionar un factor de ampliación que no aparecen en la **Magnify** herramienta, utilice las teclas de aceleración.

## <a name="to-display-or-hide-the-pixel-grid"></a>Para mostrar u ocultar la cuadrícula de píxeles

Para todos los **Editor de imágenes** paneles con un factor de ampliación de 4 o superior, puede mostrar una cuadrícula que delimita los píxeles individuales de la imagen.

1. En el **imagen** menú, seleccione **configuración de la cuadrícula**.

1. Seleccione el **cuadrícula de píxeles** casilla de verificación para mostrar la cuadrícula, o desactive la casilla para ocultar la cuadrícula.

> [!TIP]
> Información sobre herramientas aparece cuando desplaza el cursor sobre un botón de barra de herramientas. Estas sugerencias pueden ayudarle a identificar la función de cada botón.

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Teclas de aceleración](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)