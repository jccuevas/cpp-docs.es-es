---
title: Acoplar y desacoplar las barras de herramientas | Documentos de Microsoft
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
ms.openlocfilehash: 430af2344888696e3cbf053677ef59c7249b50bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352794"
---
# <a name="docking-and-floating-toolbars"></a>Barras de herramientas de acoplamiento y flotantes
La biblioteca Microsoft Foundation Class es compatible con las barras de herramientas acoplables. Una barra de herramientas acoplable puede ser, o acoplar, a cualquier lado de su ventana primaria, o se puede separar o dejarla flotando en su propia ventana de marco reducido. En este artículo se explica cómo usar las barras de herramientas acoplables en sus aplicaciones.  
  
 Si utiliza al Asistente para aplicaciones para generar el esqueleto de la aplicación, deberá elegir si desea que las barras de herramientas acoplables. De forma predeterminada, el Asistente para aplicaciones genera el código que realiza las tres acciones necesarias colocar una barra de herramientas acoplable en la aplicación:  
  
-   [Habilite el acoplamiento en una ventana de marco](#_core_enabling_docking_in_a_frame_window).  
  
-   [Habilite el acoplamiento para una barra de herramientas](#_core_enabling_docking_for_a_toolbar).  
  
-   [Acoplar la barra de herramientas (en la ventana de marco)](#_core_docking_the_toolbar).  
  
 Si falta alguno de estos pasos, la aplicación mostrará una barra de herramientas estándar. Los dos últimos pasos deben realizarse para cada barra de herramientas acoplable en la aplicación.  
  
 Otros temas tratados en este artículo son:  
  
-   [La barra de herramientas flotante](#_core_floating_the_toolbar)  
  
-   [Cambiar el tamaño de la barra de herramientas dinámicamente](#_core_dynamically_resizing_the_toolbar)  
  
-   [Establecer posiciones de ajuste para una barra de herramientas de estilo fijo](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)  
  
 Vea el ejemplo General de MFC [DOCKTOOL](../visual-cpp-samples.md) para obtener ejemplos.  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> Habilitar el acoplamiento en una ventana de marco  
 Para acoplar barras de herramientas en una ventana de marco, debe habilitarse para acoplar la ventana de marco (o destino). Esto se realiza mediante la [CFrameWnd:: EnableDocking](../mfc/reference/cframewnd-class.md#enabledocking) función, que toma una `DWORD` parámetro que es un conjunto de estilo de bits que indica qué lado de la ventana de marco acepta el acoplamiento. Si una barra de herramientas está a punto de ser acoplado y hay varios lados que se pueden acoplar a, los lados indicados en el parámetro pasado a `EnableDocking` se utilizan en el siguiente orden: superior, inferior, izquierda, derecha. Si desea poder acoplar el control de barras desde cualquier lugar, pasar `CBRS_ALIGN_ANY` a `EnableDocking`.  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> Habilitar el acoplamiento para una barra de herramientas  
 Después de haber preparado el destino de acoplamiento, debe preparar la barra de herramientas (o el origen) de un modo similar. Llame a [CControlBar:: EnableDocking](../mfc/reference/ccontrolbar-class.md#enabledocking) para cada barra de herramientas que desea acoplar, especificar el destino lados para que debe acoplar la barra de herramientas. Si no hay ninguno de los lados especificados en la llamada a `CControlBar::EnableDocking` coincide con los lados habilitados para el acoplamiento en la ventana de marco, no se puede acoplar la barra de herramientas, flotará. Una vez que se queda flotando, permanece una barra de herramientas flotante, no se puede acoplar en la ventana de marco.  
  
 Si el efecto que desee es una barra de herramientas flotante permanentemente, llame a `EnableDocking` con un parámetro de 0. A continuación, llame a [CFrameWnd:: FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar). La barra de herramientas es flotante, definitivamente no se pueden acoplar en cualquier lugar.  
  
##  <a name="_core_docking_the_toolbar"></a> Acoplar la barra de herramientas  
 Las llamadas de framework [CFrameWnd:: DockControlBar](../mfc/reference/cframewnd-class.md#dockcontrolbar) cuando el usuario intenta quitar la barra de herramientas en un lado de la ventana de marco que permite el acoplamiento.  
  
 Además, puede llamar a esta función en cualquier momento para acoplar barras de control en la ventana de marco. Esto se hace normalmente durante la inicialización. Más de una barra de herramientas se puede acoplar a un lado determinado de la ventana de marco.  
  
##  <a name="_core_floating_the_toolbar"></a> La barra de herramientas flotante  
 Separar una barra de herramientas acoplable de la ventana de marco se llama a la barra de herramientas flotante. Llame a [CFrameWnd:: FloatControlBar](../mfc/reference/cframewnd-class.md#floatcontrolbar) hacerlo. Especifique la barra de herramientas que se dejará flotando, el punto donde se va a almacenar y un estilo de alineación que determina si la barra de herramientas flotante es horizontal o vertical.  
  
 El marco de trabajo llama a esta función cuando un usuario arrastra una barra de herramientas desactivar su ubicación acoplada y lo coloca en una ubicación donde no está habilitado el acoplamiento. Esto puede ser en cualquier lugar dentro o fuera de la ventana de marco. Al igual que con `DockControlBar`, también puede llamar a esta función durante la inicialización.  
  
 La implementación de MFC de barras de herramientas acoplables no proporciona algunas de las características extendidas que se encuentran en algunas aplicaciones que admiten barras de herramientas acoplables. No se proporcionan características tales como barras de herramientas personalizables.  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> Cambiar el tamaño de la barra de herramientas dinámicamente  
 A partir de la versión 4.0 de Visual C++, se puede realizar la posible para los usuarios de la aplicación para cambiar dinámicamente el tamaño de barras de herramientas flotantes. Normalmente, una barra de herramientas tiene una forma larga, lineal, mostrar horizontalmente. Pero puede cambiar la orientación de la barra de herramientas y su forma. Por ejemplo, cuando el usuario acopla una barra de herramientas en uno de los lados verticales de la ventana de marco, la forma cambia a un diseño vertical. También es posible cambiar la forma de la barra de herramientas en un rectángulo con varias filas de botones.  
  
 Puede realizar lo siguiente:  
  
-   Especifique el cambio de tamaño dinámico como una característica de la barra de herramientas.  
  
-   Especificar el tamaño fijo como una característica de la barra de herramientas.  
  
 Para proporcionar esta compatibilidad, hay dos nuevos estilos de barra de herramientas para su uso en las llamadas a la [CToolBar:: Create](../mfc/reference/ctoolbar-class.md#create) función miembro. Son estos:  
  
-   **CBRS_SIZE_DYNAMIC** barra de controles es dinámica.  
  
-   **CBRS_SIZE_FIXED** barra de controles es fijo.  
  
 El estilo de tamaño dinámico permite al usuario cambiar el tamaño de la barra de herramientas mientras está flotando, pero no mientras está acoplada. La barra de herramientas "ajusta" cuando sea necesario para cambiar la forma cuando el usuario arrastra los bordes.  
  
 El estilo de tamaño fijo conserva los Estados de ajuste de una barra de herramientas, corregir la posición de los botones en cada columna. Usuario de la aplicación no puede cambiar la forma de la barra de herramientas. La barra de herramientas se ajusta a sitios especificados, como las ubicaciones de los separadores entre los botones. Esta forma mantiene si la barra de herramientas es acoplada o flotante. El efecto es una paleta fija con varias columnas de botones.  
  
 También puede usar [CToolBar:: GetButtonStyle](../mfc/reference/ctoolbar-class.md#getbuttonstyle) para devolver un estado y un estilo para los botones de las barras de herramientas. Estilo de un botón determina cómo aparece el botón y el modo en que responde a la entrada del usuario; el estado indica si el botón está en un estado ajustado.  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a> Establecer posiciones de ajuste para una barra de herramientas de estilo fijo  
 Para una barra de herramientas con el estilo de tamaño fijo, designe barra de herramientas de índices de botón en el que se ajustará la barra de herramientas. El código siguiente muestra cómo hacerlo en la ventana de marco principal `OnCreate` invalidar:  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]  
  
 El ejemplo General de MFC [DOCKTOOL](../visual-cpp-samples.md) muestra cómo utilizar las funciones miembro de clases [CControlBar](../mfc/reference/ccontrolbar-class.md) y [CToolBar](../mfc/reference/ctoolbar-class.md) para administrar el diseño dinámico de una barra de herramientas. Vea el archivo EDITBAR. CPP en DOCKTOOL.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Aspectos básicos de la barra de herramientas](../mfc/toolbar-fundamentals.md)  
  
-   [Información sobre herramientas de barra de herramientas](../mfc/toolbar-tool-tips.md)  
  
-   [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

