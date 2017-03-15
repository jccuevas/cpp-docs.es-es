---
title: "Barras de herramientas acopladas y flotantes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBRS_SIZE_DYNAMIC"
  - "CBRS_SIZE_FIXED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBRS_ALIGN_ANY (constante)"
  - "CBRS_SIZE_DYNAMIC (constante)"
  - "CBRS_SIZE_FIXED (constante)"
  - "barras de herramientas de tamaño fijo"
  - "paletas flotantes"
  - "barras de herramientas flotantes"
  - "ventanas de marco, barras de herramientas de acoplamiento"
  - "paletas, flotante"
  - "tamaño"
  - "tamaño, barras de herramientas"
  - "controles de barra de herramientas [MFC], contener"
  - "barras de herramientas [C++], acoplar"
  - "barras de herramientas [C++], flotante"
  - "barras de herramientas [C++], tamaño"
  - "barras de herramientas [C++], contener"
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Barras de herramientas acopladas y flotantes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca Microsoft Foundation Class admite las barras de herramientas acoplables.  Una barra de herramientas acoplable puede ser asociada, o acoplar, a cualquier lado de la ventana primaria, o el posible desasociado, o dejarla flotando, en su propia ventana de mini\- cuadro.  En este artículo se explica cómo utilizar las barras de herramientas acoplables en las aplicaciones.  
  
 Si utiliza el Asistente para aplicaciones para generar la estructura de la aplicación, se le elegir si desea que las barras de herramientas acoplables.  De forma predeterminada, el Asistente para aplicaciones genera código que realiza los tres acciones necesarios para colocar una barra de herramientas acoplable en la aplicación:  
  
-   [Acoplamiento de permisos en una ventana de marco](#_core_enabling_docking_in_a_frame_window).  
  
-   [Acoplamiento de permiso de una barra de herramientas](#_core_enabling_docking_for_a_toolbar).  
  
-   [Acople la barra de herramientas \(a la ventana de marco\)](#_core_docking_the_toolbar).  
  
 Si faltan cualquiera de estos pasos, la aplicación mostrará una barra de herramientas estándar.  Los dos últimos pasos se deben realizar para cada barra de herramientas acoplable dentro de la aplicación.  
  
 Otros temas cubiertos en incluyen de caso:  
  
-   [Flotante de la barra de herramientas](#_core_floating_the_toolbar)  
  
-   [Dinámicamente el tamaño de la barra de herramientas](#_core_dynamically_resizing_the_toolbar)  
  
-   [Establecer las posiciones de ajuste de una barra de herramientas de corregir\- estilo](#_core_setting_wrap_positions_for_a_fixed.2d.style_toolbar)  
  
 Vea el ejemplo [DOCKTOOL](../top/visual-cpp-samples.md) MFC General para los ejemplos.  
  
##  <a name="_core_enabling_docking_in_a_frame_window"></a> Habilitar el acoplamiento en una ventana de marco  
 Para acoplar barras de herramientas a una ventana de marco, la ventana de marco \(o destino\) se debe habilitar para permitir acoplamiento.  Esto se hace utilizando la función de [CFrameWnd::EnableDocking](../Topic/CFrameWnd::EnableDocking.md) , que toma un parámetro de `DWORD` que es un conjunto de indicación de los bits de estilo qué lado de la ventana de marco acepta el acoplamiento.  Si una barra de herramientas está a punto de ser acoplada y hay lados multiproceso que puede acoplarse a, los lados indicados en el parámetro pasado a `EnableDocking` se utilizan en el orden siguiente: parte superior, inferior, izquierdo, derecho.  Si desea poder acoplar barras de controles en cualquier punto, pase `CBRS_ALIGN_ANY` a `EnableDocking`.  
  
##  <a name="_core_enabling_docking_for_a_toolbar"></a> Habilitar el acoplamiento de una barra de herramientas  
 Después de haber preparado el destino para acoplar, debe preparar la barra de herramientas \(o el origen\) de manera similar.  Llamada [CControlBar::EnableDocking](../Topic/CControlBar::EnableDocking.md) para cada barra de herramientas que desee acoplar, especificando los extremos de destino a los que desea acoplar la barra de herramientas.  Si ninguno de los lados especificados en la llamada a la coincidencia de `CControlBar::EnableDocking` los lados habilitados para acoplar en la ventana de marco, la barra de herramientas no pueden acoplar — flotarán.  Cuando queda flotando, permanece como una barra de herramientas flotante, incapaz de acoplarse a la ventana de marco.  
  
 Si el efecto deseado es permanentemente una barra de herramientas flotante, llama a `EnableDocking` con un parámetro de 0.  A continuación llamada [CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md).  La barra de herramientas permanece flotante, permanentemente incapaz de acoplarse en cualquier sitio.  
  
##  <a name="_core_docking_the_toolbar"></a> Acoplar la barra de herramientas  
 El marco de trabajo llama a [CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md) cuando el usuario intenta quitar la barra de herramientas en el lado de la ventana de marco que permite acoplamiento.  
  
 Además, puede llamar a esta función en cualquier momento para acoplar barras de controles en la ventana de marco.  Esto se hace normalmente durante la inicialización.  Más de una barra de herramientas se puede acoplar a un lado determinado de la ventana de marco.  
  
##  <a name="_core_floating_the_toolbar"></a> Flotante de la barra de herramientas  
 Desasociando una barra de herramientas acoplable de la ventana de marco se denomina flotación de la barra de herramientas.  Llamada [CFrameWnd::FloatControlBar](../Topic/CFrameWnd::FloatControlBar.md) para ello.  Especifique la barra de herramientas que se flotarán, el punto donde debe ser colocada, y un estilo de alineación que determina si la barra de herramientas flotante es horizontal o vertical.  
  
 El marco de trabajo llama a esta función cuando un usuario arrastra una barra de herramientas de su ubicación acoplada y colóquelo en una ubicación donde el acoplar no está habilitada.  Esto puede estar en cualquier parte dentro o fuera de la ventana de marco.  Como con `DockControlBar`, también puede llamar a esta función durante la inicialización.  
  
 Implementación de MFC de las barras de herramientas acoplables no proporciona algunas características extendidas encontradas en algunas aplicaciones que admiten las barras de herramientas acoplables.  Las características como barras de herramientas personalizables no se proporcionan.  
  
##  <a name="_core_dynamically_resizing_the_toolbar"></a> Dinámicamente de tamaño de la barra de herramientas  
 A partir de la versión 4.0 de Visual C\+\+, puede crearla posible para los usuarios de la aplicación para cambiar el tamaño de las barras de herramientas flotante dinámicamente.  Normalmente, una barra de herramientas tiene una forma larga, lineal, mostrará horizontalmente.  Pero puede cambiar la forma de la barra de herramientas orientación y.  Por ejemplo, cuando el usuario acopla una barra de herramientas con uno de los lados verticales de la ventana de marco, cambia la forma a un diseño vertical.  También es posible volver a dar forma la barra de herramientas en un rectángulo con varias filas de botones.  
  
 Puede realizar lo siguiente:  
  
-   Especifique el tamaño dinámico como característica de la barra de herramientas.  
  
-   Especifique corregido el tamaño como una característica de la barra de herramientas.  
  
 Para proporcionar esta compatibilidad, hay dos nuevos estilos de la barra de herramientas para su uso en las llamadas a la función miembro de [CToolBar::Create](../Topic/CToolBar::Create.md) .  Son estos:  
  
-   Barra de control de**CBRS\_SIZE\_DYNAMIC**es dinámica.  
  
-   Se corrige la barra de control de**CBRS\_SIZE\_FIXED**.  
  
 El estilo dinámico de tamaño permite al usuario cambiar el tamaño de la barra de herramientas cuando es flotante, pero no mientras está acoplado.  La barra de herramientas “ajusta” cuando sea necesario desformar como arrastres de usuario los bordes.  
  
 El estilo corregido tamaño conserva los estados de ajuste de una barra de herramientas, corrigiendo la posición de cada columna.  El usuario de la aplicación no puede cambiar la forma de la barra de herramientas.  Los ajustes de la barra de herramientas en los lugares notificados, como las ubicaciones de separadores entre los botones.  Mantiene esta forma si la barra de herramientas está acoplada o flotante.  El efecto es una paleta fija con varias columnas de botones.  
  
 También puede utilizar [CToolBar::GetButtonStyle](../Topic/CToolBar::GetButtonStyle.md) para devolver un estado y un estilo para los botones de las barras de herramientas.  El estilo de un botón determina cómo aparece el botón y cómo responde a los datos proporcionados por el usuario; el estado indica si el botón está en un estado ajustada.  
  
##  <a name="_core_setting_wrap_positions_for_a_fixed.2d.style_toolbar"></a> Establecer el ajuste las posiciones de una barra de herramientas de Corregir\- estilo  
 Para una barra de herramientas con el estilo corregido tamaño, índices denominados del botón de la barra de herramientas en los que la barra de herramientas se ajustarán.  El código siguiente muestra cómo hacerlo en la invalidación de `OnCreate` de la ventana de marco principal:  
  
 [!code-cpp[NVC_MFCDocViewSDI#10](../mfc/codesnippet/CPP/docking-and-floating-toolbars_1.cpp)]  
  
 El ejemplo [DOCKTOOL](../top/visual-cpp-samples.md) MFC General muestra cómo utilizar funciones miembro de clases [CControlBar](../mfc/reference/ccontrolbar-class.md) y [CToolBar](../mfc/reference/ctoolbar-class.md) para administrar el diseño dinámico de una barra de herramientas.  Vea el archivo EDITBAR.CPP en DOCKTOOL.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Fundamentos de la barra de herramientas](../mfc/toolbar-fundamentals.md)  
  
-   [Información sobre herramientas de la barra de herramientas](../mfc/toolbar-tool-tips.md)  
  
-   [Mediante las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
## Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)