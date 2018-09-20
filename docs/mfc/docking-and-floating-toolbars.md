---
title: Acoplar y desacoplar las barras de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95990ef4f1d2b1c6eb4278f645226e57b67e15e8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399033"
---
# <a name="docking-and-floating-toolbars"></a>Barras de herramientas de acoplamiento y flotantes

La biblioteca Microsoft Foundation Class es compatible con las barras de herramientas acoplables. Una barra de herramientas acoplable puede ser, o acoplar, a cualquier lado de su ventana primaria, o se puede desasociar o flotando en su propia ventana de marco reducido. En este artículo se explica cómo usar las barras de herramientas acoplables en sus aplicaciones.

Si usa al Asistente para aplicaciones para generar el esqueleto de la aplicación, deberá elegir si desea que las barras de herramientas acoplables. De forma predeterminada, el Asistente para la aplicación genera el código que realiza las tres acciones necesarias colocar una barra de herramientas acoplable en la aplicación:

- [Habilite el acoplamiento en una ventana de marco](#_core_enabling_docking_in_a_frame_window).

- [Habilite el acoplamiento de una barra de herramientas](#_core_enabling_docking_for_a_toolbar).

- [Acoplar la barra de herramientas (en la ventana de marco)](#_core_docking_the_toolbar).

Si falta alguno de estos pasos, la aplicación mostrará una barra de herramientas estándar. Los dos últimos pasos deben realizarse para cada barra de herramientas acoplable en la aplicación.

Otros temas tratados en este artículo incluyen:

- [La barra de herramientas flotante](#_core_floating_the_toolbar)

- [Cambiar el tamaño de la barra de herramientas dinámicamente](#_core_dynamically_resizing_the_toolbar)

- [Establecer posiciones de ajuste para una barra de herramientas de estilo fijo](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Vea el ejemplo General de MFC [DOCKTOOL](../visual-cpp-samples.md) para obtener ejemplos.

##  <a name="_core_enabling_docking_in_a_frame_window"></a> Habilitar el acoplamiento en una ventana de marco

Para acoplar las barras de herramientas en una ventana de marco, debe habilitarse para acoplar la ventana de marco (o destino). Esto se realiza mediante el [CFrameWnd:: EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) función, que toma una *DWORD* parámetro que es un conjunto de estilos de bits que indica qué lado de la ventana de marco acepta el acoplamiento. Si es acoplar una barra de herramientas y hay varias partes que se pueden acoplar a, los lados indicados en el parámetro pasado a `EnableDocking` se usan en el siguiente orden: superior, inferior, izquierda, derecha. Si desea poder acoplar el control de las barras desde cualquier lugar, pase **CBRS_ALIGN_ANY** a `EnableDocking`.

##  <a name="_core_enabling_docking_for_a_toolbar"></a> Habilitar el acoplamiento de una barra de herramientas

Después de haber preparado el destino de acoplamiento, debe preparar la barra de herramientas (o el origen) de forma similar. Llame a [CControlBar:: EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) para cada barra de herramientas que desee acoplar, especificar el destino lados para lo que debe acoplar la barra de herramientas. Si ninguno de los lados especificados en la llamada a `CControlBar::EnableDocking` coinciden con los lados habilitados para el acoplamiento en la ventana de marco, no se puede acoplar la barra de herramientas, se hará flotante. Una vez que queda flotando, permanece una barra de herramientas flotante, no se puede acoplar a la ventana de marco.

Si el efecto deseado es una barra de herramientas flotante permanentemente, llame a `EnableDocking` con un parámetro de 0. A continuación, llame a [CFrameWnd:: FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). Sigue siendo la barra de herramientas flotante, de forma permanente no se puede acoplar en cualquier lugar.

##  <a name="_core_docking_the_toolbar"></a> Acoplar la barra de herramientas

Las llamadas de framework [CFrameWnd:: DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) cuando el usuario intenta quitar la barra de herramientas en un lado de la ventana de marco que permite el acoplamiento.

Además, puede llamar a esta función en cualquier momento para acoplar barras de control a la ventana de marco. Normalmente, esto se realiza durante la inicialización. Más de una barra de herramientas se puede acoplar a un lado determinado de la ventana de marco.

##  <a name="_core_floating_the_toolbar"></a> La barra de herramientas flotante

Desasociar una barra de herramientas acoplable de la ventana de marco se llama a la barra de herramientas flotante. Llame a [CFrameWnd:: FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) para hacerlo. Especifique un estilo de alineación que determina si la barra de herramientas flotante es horizontal o vertical, el punto donde debe colocarse y la barra de herramientas a flotar.

El marco de trabajo llama a esta función cuando el usuario arrastra una barra de herramientas fuera de su ubicación acoplada y lo coloca en una ubicación que no está habilitado el acoplamiento. Esto puede ser en cualquier lugar dentro o fuera de la ventana de marco. Igual que con `DockControlBar`, también puede llamar a esta función durante la inicialización.

La implementación de MFC de barras de herramientas acoplables no proporciona algunas de las características extendidas que se encuentran en algunas aplicaciones que admiten las barras de herramientas acoplables. No se proporcionan características como las barras de herramientas personalizables.

##  <a name="_core_dynamically_resizing_the_toolbar"></a> Cambiar el tamaño de la barra de herramientas dinámicamente

A partir de Visual C++ versión 4.0, puede hacerlo posible para los usuarios de la aplicación para cambiar dinámicamente el tamaño de las barras de herramientas flotantes. Normalmente, una barra de herramientas tiene una forma larga, lineal, mostrar horizontalmente. Pero puede cambiar la orientación de la barra de herramientas y la forma. Por ejemplo, cuando el usuario acopla una barra de herramientas en uno de los lados verticales de la ventana de marco, la forma cambia a un diseño vertical. También es posible cambiar la forma de la barra de herramientas en un rectángulo con varias filas de botones.

Puede realizar lo siguiente:

- Especificar el cambio de tamaño dinámico como una característica de la barra de herramientas.

- Especificar un tamaño fijo como una característica de la barra de herramientas.

Para proporcionar esta compatibilidad, hay dos nuevos estilos de barra de herramientas para su uso en las llamadas a la [CToolBar:: Create](../mfc/reference/ctoolbar-class.md#create) función miembro. Son estos:

- **CBRS_SIZE_DYNAMIC** barra de Control es dinámico.

- **CBRS_SIZE_FIXED** se ha corregido la barra de Control.

El estilo de tamaño dinámico permite al usuario cambiar el tamaño de la barra de herramientas mientras está flotando, pero no cuando está acoplado. La barra de herramientas "ajusta" cuando sea necesario para cambiar la forma cuando el usuario arrastra sus bordes.

El estilo de tamaño fijo conserva los Estados de ajuste de una barra de herramientas, corregir la posición de los botones en cada columna. Usuario de la aplicación no puede cambiar la forma de la barra de herramientas. La barra de herramientas se ajusta a los sitios especificados, como las ubicaciones de los separadores entre los botones. Esta forma mantiene si la barra de herramientas está acoplada o flotante. El efecto es una paleta fija con varias columnas de botones.

También puede usar [CToolBar:: GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) para devolver un estado y un estilo para los botones de las barras de herramientas. Estilo de un botón determina cómo aparece el botón y cómo responde a la entrada del usuario; el estado indica si el botón está en un estado ajustado.

##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Establecer posiciones de ajuste para una barra de herramientas de estilo fijo

Para una barra de herramientas con el estilo de tamaño fijo, designar la barra de herramientas de los índices de botón en el que se ajustará la barra de herramientas. El código siguiente muestra cómo hacer esto en la ventana de marco principal `OnCreate` invalidar:

[!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

El ejemplo General de MFC [DOCKTOOL](../visual-cpp-samples.md) se muestra cómo utilizar las funciones miembro de clases [CControlBar](../mfc/reference/ccontrolbar-class.md) y [CToolBar](../mfc/reference/ctoolbar-class.md) para administrar el diseño dinámico de una barra de herramientas. Vea el archivo EDITBAR. CPP en DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Aspectos básicos de la barra de herramientas](../mfc/toolbar-fundamentals.md)

- [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)

- [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Vea también

[Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

