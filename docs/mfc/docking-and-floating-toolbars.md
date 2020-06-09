---
title: Barras de herramientas de acoplamiento y flotantes
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: f40d8860f2e514bf3c9e9364a664326250c9627a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615832"
---
# <a name="docking-and-floating-toolbars"></a>Barras de herramientas de acoplamiento y flotantes

El biblioteca MFC admite barras de herramientas acoplables. Se puede adjuntar o acoplar una barra de herramientas acoplable a cualquier lado de la ventana primaria, o bien se puede desasociar o flotar en su propia ventana de marco reducido. En este artículo se explica cómo usar las barras de herramientas acoplables en las aplicaciones.

Si usa el Asistente para aplicaciones para generar el esqueleto de la aplicación, se le pedirá que elija si desea usar barras de herramientas acoplables. De forma predeterminada, el Asistente para aplicaciones genera el código que realiza las tres acciones necesarias para colocar una barra de herramientas acoplable en la aplicación:

- [Habilite el acoplamiento en una ventana de marco](#_core_enabling_docking_in_a_frame_window).

- [Habilite el acoplamiento de una barra de herramientas](#_core_enabling_docking_for_a_toolbar).

- [Acople la barra de herramientas (a la ventana de marco)](#_core_docking_the_toolbar).

Si falta alguno de estos pasos, la aplicación mostrará una barra de herramientas estándar. Los dos últimos pasos se deben realizar para cada barra de herramientas acoplable en la aplicación.

Otros temas que se tratan en este artículo son:

- [Flotar la barra de herramientas](#_core_floating_the_toolbar)

- [Cambiar el tamaño de la barra de herramientas dinámicamente](#_core_dynamically_resizing_the_toolbar)

- [Establecer posiciones de ajuste para una barra de herramientas de estilo fijo](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Vea el ejemplo general de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) para obtener ejemplos.

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Habilitar el acoplamiento en una ventana de marco

Para acoplar barras de herramientas a una ventana de marco, la ventana de marco (o destino) debe estar habilitada para permitir el acoplamiento. Esto se hace mediante la función [CFrameWnd:: EnableDocking](reference/cframewnd-class.md#enabledocking) , que toma un parámetro *DWORD* que es un conjunto de bits de estilo que indica qué lado de la ventana de marco acepta el acoplamiento. Si una barra de herramientas está a punto de acoplarse y hay varios lados en los que se podría acoplar, los lados indicados en el parámetro pasado `EnableDocking` se usan en el siguiente orden: superior, inferior, izquierda, derecha. Si desea poder acoplar las barras de control en cualquier lugar, pase **CBRS_ALIGN_ANY** a `EnableDocking` .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Habilitar el acoplamiento de una barra de herramientas

Una vez que haya preparado el destino para el acoplamiento, debe preparar la barra de herramientas (u origen) de manera similar. Llame a [CControlBar:: EnableDocking](reference/ccontrolbar-class.md#enabledocking) para cada barra de herramientas que desee acoplar, especificando los lados del destino en los que se debe acoplar la barra de herramientas. Si ninguno de los lados especificados en la llamada `CControlBar::EnableDocking` coincide con los lados habilitados para el acoplamiento en la ventana de marco, la barra de herramientas no se puede acoplar; será flotante. Una vez que se ha flotado, sigue siendo una barra de herramientas flotante, no se puede acoplar a la ventana de marco.

Si el efecto que desea es una barra de herramientas flotante permanente, llame a `EnableDocking` con un parámetro de 0. Después, llame a [CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar). La barra de herramientas permanece flotante, no se puede acoplar permanentemente en cualquier lugar.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Acoplar la barra de herramientas

El marco de trabajo llama a [CFrameWnd::D ockcontrolbar](reference/cframewnd-class.md#dockcontrolbar) cuando el usuario intenta quitar la barra de herramientas en un lado de la ventana de marco que permite el acoplamiento.

Además, puede llamar a esta función en cualquier momento para acoplar las barras de control a la ventana de marco. Esto se hace normalmente durante la inicialización. Se puede acoplar más de una barra de herramientas a un lado determinado de la ventana de marco.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Flotar la barra de herramientas

Desasociar una barra de herramientas acoplable de la ventana de marco se denomina flotante en la barra de herramientas. Llame a [CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar) para hacerlo. Especifique la barra de herramientas que se va a flotar, el punto en el que debe colocarse y un estilo de alineación que determine si la barra de herramientas flotante es horizontal o vertical.

El marco de trabajo llama a esta función cuando un usuario arrastra una barra de herramientas fuera de su ubicación acoplada y la coloca en una ubicación donde no está habilitado el acoplamiento. Puede ser cualquier parte dentro o fuera de la ventana de marco. Como con `DockControlBar` , también puede llamar a esta función durante la inicialización.

La implementación de MFC de las barras de herramientas acoplables no proporciona algunas de las características extendidas que se encuentran en algunas aplicaciones que admiten barras de herramientas acoplables. No se proporcionan características como las barras de herramientas personalizables.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Cambiar el tamaño de la barra de herramientas dinámicamente

A partir de Visual C++ versión 4,0, puede permitir que los usuarios de la aplicación cambien dinámicamente el tamaño de las barras de herramientas flotantes. Normalmente, una barra de herramientas tiene una forma larga y lineal, que se muestra horizontalmente. Sin embargo, puede cambiar la orientación de la barra de herramientas y su forma. Por ejemplo, cuando el usuario acopla una barra de herramientas a uno de los lados verticales de la ventana de marco, la forma cambia a un diseño vertical. También es posible remodelar la barra de herramientas en un rectángulo con varias filas de botones.

Puede:

- Especifique el tamaño dinámico como una característica de la barra de herramientas.

- Especifique un tamaño fijo como una característica de la barra de herramientas.

Para proporcionar esta compatibilidad, hay dos nuevos estilos de barra de herramientas que se pueden usar en las llamadas a la función miembro [CToolBar:: Create](reference/ctoolbar-class.md#create) . Son las siguientes:

- **CBRS_SIZE_DYNAMIC** La barra de control es dinámica.

- **CBRS_SIZE_FIXED** La barra de control es fija.

El estilo Dynamic size permite que el usuario cambie el tamaño de la barra de herramientas mientras esté flotante, pero no mientras esté acoplada. La barra de herramientas "ajusta" cuando es necesario para cambiar la forma a medida que el usuario arrastra los bordes.

El estilo fijo de tamaño conserva el estado de ajuste de una barra de herramientas, corrigiendo la posición de los botones en cada columna. El usuario de la aplicación no puede cambiar la forma de la barra de herramientas. La barra de herramientas se ajusta en los lugares designados, como las ubicaciones de los separadores entre los botones. Mantiene esta forma si la barra de herramientas está acoplada o flotante. El efecto es una paleta fija con varias columnas de botones.

También puede usar [CToolBar:: GetButtonStyle](reference/ctoolbar-class.md#getbuttonstyle) para devolver un estado y un estilo para los botones de las barras de herramientas. El estilo de un botón determina cómo aparece el botón y cómo responde a los datos proporcionados por el usuario; el estado indica si el botón está en un estado ajustado.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Establecer posiciones de ajuste para una barra de herramientas de estilo fijo

En el caso de una barra de herramientas con el estilo tamaño fijo, designe los índices de botón de la barra de herramientas en los que se ajustará la barra de herramientas. En el código siguiente se muestra cómo hacer esto en la invalidación de la ventana de marco principal `OnCreate` :

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

En el ejemplo general de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) se muestra cómo usar las funciones miembro de las clases [CControlBar](reference/ccontrolbar-class.md) y [CToolBar](reference/ctoolbar-class.md) para administrar el diseño dinámico de una barra de herramientas. Vea el archivo EDITBAR. CPP en DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Aspectos básicos de las barras de herramientas](toolbar-fundamentals.md)

- [Información sobre herramientas de barra de herramientas](toolbar-tool-tips.md)

- [Usar las barras de herramientas anteriores](using-your-old-toolbars.md)

## <a name="see-also"></a>Consulte también

[Implementación de barra de herramientas de MFC](mfc-toolbar-implementation.md)
