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
ms.openlocfilehash: 30113565167b96b0df84a65768a1dfabe92ceffe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369767"
---
# <a name="docking-and-floating-toolbars"></a>Barras de herramientas de acoplamiento y flotantes

La biblioteca Microsoft Foundation Class admite barras de herramientas acoplables. Una barra de herramientas acoplable se puede adjuntar, o acoplar, a cualquier lado de su ventana primaria, o se puede separar, o flotar, en su propia ventana de marco pequeño. En este artículo se explica cómo utilizar barras de herramientas acoplables en las aplicaciones.

Si utiliza el Asistente para aplicaciones para generar el esqueleto de la aplicación, se le pedirá que elija si desea barras de herramientas acoplables. De forma predeterminada, el Asistente para aplicaciones genera el código que realiza las tres acciones necesarias para colocar una barra de herramientas acoplable en la aplicación:

- [Habilite el acoplamiento en una ventana de marco.](#_core_enabling_docking_in_a_frame_window)

- [Habilite el acoplamiento para una barra de herramientas](#_core_enabling_docking_for_a_toolbar).

- [Acople la barra de herramientas (a la ventana de marco).](#_core_docking_the_toolbar)

Si falta alguno de estos pasos, la aplicación mostrará una barra de herramientas estándar. Los dos últimos pasos se deben realizar para cada barra de herramientas acoplable de la aplicación.

Otros temas tratados en este artículo incluyen:

- [Flotando en la barra de herramientas](#_core_floating_the_toolbar)

- [Cambiar el tamaño dinámico de la barra de herramientas](#_core_dynamically_resizing_the_toolbar)

- [Configuración de posiciones de ajuste para una barra de herramientas de estilo fijo](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Vea el ejemplo general de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) para obtener ejemplos.

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Habilitación del acoplamiento en una ventana de marco

Para acoplar barras de herramientas a una ventana de marco, la ventana de marco (o destino) debe estar habilitada para permitir el acoplamiento. Esto se hace mediante la función [CFrameWnd::EnableDocking,](../mfc/reference/cframewnd-class.md#enabledocking) que toma un parámetro *DWORD* que es un conjunto de bits de estilo que indican qué lado de la ventana de marco acepta el acoplamiento. Si una barra de herramientas está a punto de acoplarse y hay varios lados a los que se podría acoplar, los lados indicados en el parámetro pasado `EnableDocking` se utilizan en el siguiente orden: superior, inferior, izquierda, derecha. Si desea poder acoplar barras **CBRS_ALIGN_ANY** de `EnableDocking`control en cualquier lugar, pase CBRS_ALIGN_ANY a .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Habilitación del acoplamiento para una barra de herramientas

Después de haber preparado el destino para el acoplamiento, debe preparar la barra de herramientas (o origen) de una manera similar. Llame a [CControlBar::EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) para cada barra de herramientas que desea acoplar, especificando los lados de destino a los que debe acoplar la barra de herramientas. Si ninguno de los lados `CControlBar::EnableDocking` especificados en la llamada para que coincida con los lados habilitados para el acoplamiento en la ventana de marco, la barra de herramientas no puede acoplar — flotará. Una vez que se ha flotado, sigue siendo una barra de herramientas flotante, no se puede acoplar a la ventana de marco.

Si el efecto que desea es una `EnableDocking` barra de herramientas flotante permanentemente, llame con un parámetro de 0. A continuación, llame a [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). La barra de herramientas permanece flotante, permanentemente incapaz de acoplarse en cualquier lugar.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Acoplamiento de la barra de herramientas

El marco de trabajo llama [a CFrameWnd::DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) cuando el usuario intenta quitar la barra de herramientas en un lado de la ventana de marco que permite el acoplamiento.

Además, puede llamar a esta función en cualquier momento para acoplar las barras de control a la ventana de marco. Esto se hace normalmente durante la inicialización. Se puede acoplar más de una barra de herramientas a un lado determinado de la ventana de marco.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Flotando la barra de herramientas

Separar una barra de herramientas acoplable de la ventana de marco se denomina flotar la barra de herramientas. Llame a [CFrameWnd::FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) para hacer esto. Especifique la barra de herramientas que se va a flotar, el punto donde se debe colocar y un estilo de alineación que determina si la barra de herramientas flotante es horizontal o vertical.

El marco de trabajo llama a esta función cuando un usuario arrastra una barra de herramientas fuera de su ubicación acoplada y la coloca en una ubicación donde el acoplamiento no está habilitado. Esto puede estar en cualquier lugar dentro o fuera de la ventana de marco. Al `DockControlBar`igual que con , también puede llamar a esta función durante la inicialización.

La implementación MFC de barras de herramientas acoplables no proporciona algunas de las características extendidas que se encuentran en algunas aplicaciones que admiten barras de herramientas acoplables. No se proporcionan características como barras de herramientas personalizables.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Cambiar el tamaño dinámico de la barra de herramientas

A partir de Visual C++ versión 4.0, puede hacer posible que los usuarios de la aplicación redimensionen dinámicamente las barras de herramientas flotantes. Normalmente, una barra de herramientas tiene una forma larga y lineal, que se muestra horizontalmente. Pero puede cambiar la orientación de la barra de herramientas y su forma. Por ejemplo, cuando el usuario acopla una barra de herramientas contra uno de los lados verticales de la ventana de marco, la forma cambia a un diseño vertical. También es posible cambiar la forma de la barra de herramientas en un rectángulo con varias filas de botones.

Puede:

- Especifique el tamaño dinámico como característica de la barra de herramientas.

- Especifique el tamaño fijo como característica de la barra de herramientas.

Para proporcionar esta compatibilidad, hay dos nuevos estilos de barra de herramientas para su uso en las llamadas a la [CToolBar::Create](../mfc/reference/ctoolbar-class.md#create) función miembro. Son las siguientes:

- **CBRS_SIZE_DYNAMIC** La barra de control es dinámica.

- **CBRS_SIZE_FIXED** La barra de control está fija.

El estilo dinámico de tamaño permite al usuario cambiar el tamaño de la barra de herramientas mientras está flotante, pero no mientras está acoplada. La barra de herramientas "envuelve" donde sea necesario para cambiar la forma a medida que el usuario arrastra sus bordes.

El estilo fijo de tamaño conserva los estados de ajuste de una barra de herramientas, fijando la posición de los botones en cada columna. El usuario de la aplicación no puede cambiar la forma de la barra de herramientas. La barra de herramientas se ajusta en lugares designados, como las ubicaciones de los separadores entre los botones. Mantiene esta forma si la barra de herramientas está acoplada o flotante. El efecto es una paleta fija con varias columnas de botones.

También puede usar [CToolBar::GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) para devolver un estado y un estilo para los botones de las barras de herramientas. El estilo de un botón determina cómo aparece el botón y cómo responde a la entrada del usuario; el estado indica si el botón está en un estado ajustado.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Configuración de posiciones de ajuste para una barra de herramientas de estilo fijo

Para una barra de herramientas con el estilo fijo de tamaño, designe índices de botones de barra de herramientas en los que se ajustará la barra de herramientas. El código siguiente muestra cómo hacerlo en la `OnCreate` invalidación de la ventana de marco principal:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

El ejemplo general de MFC [DOCKTOOL](../overview/visual-cpp-samples.md) muestra cómo utilizar las funciones miembro de las clases [CControlBar](../mfc/reference/ccontrolbar-class.md) y [CToolBar](../mfc/reference/ctoolbar-class.md) para administrar el diseño dinámico de una barra de herramientas. Consulte el archivo EDITBAR. CPP en DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Fundamentos de la barra de herramientas](../mfc/toolbar-fundamentals.md)

- [Consejos de herramientas de la barra de herramientas](../mfc/toolbar-tool-tips.md)

- [Uso de las barras de herramientas antiguas](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Consulte también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)
