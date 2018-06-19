---
title: Información sobre herramientas de barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7024284a1be22aed211e8cf58f8366df88aa917
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383502"
---
# <a name="toolbar-tool-tips"></a>Información sobre herramientas de la barra de herramientas
Información sobre herramientas es esa pequeña ventana emergente que muestra una breve descripción del propósito de un botón de barra de herramientas cuando coloca el mouse sobre un botón durante un período de tiempo. Cuando se crea una aplicación con el Asistente para la aplicación que tiene una barra de herramientas, se proporciona compatibilidad con información sobre la herramienta para usted. Este artículo explica tanto la información sobre compatibilidad con herramientas creado por el Asistente para aplicaciones y cómo agregar compatibilidad con la sugerencia de herramienta a la aplicación.  
  
 En este artículo se tratan los aspectos siguientes:  
  
-   [Activar información sobre herramientas](#_core_activating_tool_tips)  
  
-   [Actualizaciones de barra de estado por proximidad](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> Activar información sobre herramientas  
 Para activar la información sobre herramientas en la aplicación, debe hacer dos cosas:  
  
-   Agregar el `CBRS_TOOLTIPS` estilo a los demás estilos (como **WS_CHILD**, **WS_VISIBLE**y otros **CBRS_** estilos) pasa como el `dwStyle` parámetro para el [ CToolBar:: Create](../mfc/reference/ctoolbar-class.md#create) función o en [SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle).  
  
-   Como se describe en el procedimiento siguiente, anexe el texto de sugerencia de la barra de herramientas, separado por un carácter de nueva línea ('\n'), para el recurso de cadena que contiene el símbolo del sistema de línea de comandos para el comando de barra de herramientas. El recurso de cadena comparte el identificador del botón de barra de herramientas.  
  
#### <a name="to-add-the-tool-tip-text"></a>Para agregar el texto de información sobre herramientas  
  
1.  Mientras se edita la barra de herramientas en el editor de la barra de herramientas, abra la **propiedades de botón de barra de herramientas** ventana de un botón determinado.  
  
2.  En el **Prompt** , especifique el texto que desea que aparezcan en la información sobre herramientas para ese botón.  
  
> [!NOTE]
>  Si se establece el texto como una propiedad de botón en el editor de la barra de herramientas reemplaza el procedimiento anterior, en el que tenía que abrir y editar el recurso de cadena.  
  
 Si una barra de controles con información sobre herramientas habilitada contiene controles secundarios en él, la barra de control mostrará una información sobre herramientas para cada control secundario en la barra de control mientras cumple los criterios siguientes:  
  
-   El identificador del control no - es 1.  
  
-   La entrada de tabla de cadenas con el mismo identificador que el control secundario en el archivo de recursos tiene una cadena de información sobre herramientas.  
  
##  <a name="_core_fly_by_status_bar_updates"></a> Actualizaciones de la barra de estado por proximidad  
 Una característica relacionada con la información sobre herramientas es estado "por proximidad" actualización de la barra. De forma predeterminada, el mensaje en la barra de estado describe sólo un botón de barra de herramientas determinada cuando se activa el botón. Mediante la inclusión de `CBRS_FLYBY` en la lista de estilos que se pasan a `CToolBar::Create`, puede tener actualizar estos mensajes cuando el cursor del mouse pasa por encima de la barra de herramientas sin activar realmente el botón.  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Implementación de la barra de herramientas de MFC (información general de las barras de herramientas)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Acoplar y desacoplar las barras de herramientas](../mfc/docking-and-floating-toolbars.md)  
  
-   El [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) clases  
  
-   [Trabajar con el control de barra de herramientas](../mfc/working-with-the-toolbar-control.md)  
  
-   [Uso de las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)

