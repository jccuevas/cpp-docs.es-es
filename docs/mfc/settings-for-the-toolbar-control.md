---
title: Configuración del Control de barra de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], about toolbar controls
- CToolBarCtrl class [MFC], settings
ms.assetid: 025ba920-b3ee-4d82-9367-e652cd7875b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81631ba25f898e3740b82c0fab9d5af5da930117
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373365"
---
# <a name="settings-for-the-toolbar-control"></a>Configuración del control Toolbar

Los botones de barra de herramientas pueden mostrar un mapa de bits, una cadena o ambos. De forma predeterminada, el tamaño de la imagen se establece en las dimensiones de 16 por 15 píxeles. Todos los botones tienen el mismo ancho, en píxeles del 24 por 22 predeterminado. Alto de la barra de herramientas viene determinada por el alto de los botones y ancho de la barra de herramientas es el mismo que el ancho del área de cliente de la ventana primaria, también de forma predeterminada.

Una barra de herramientas puede tener características de personalización integradas, incluyendo un cuadro de diálogo de personalización definido por el sistema, que permiten al usuario insertar, eliminar o reorganizar botones de barra de herramientas. Una aplicación determina si las características de personalización están disponibles para el usuario y controla la medida a la que el usuario puede personalizar la barra de herramientas. Para obtener más información acerca de cómo personalizar la barra de herramientas, vea la clase [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) en el *referencia de MFC*.

## <a name="see-also"></a>Vea también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

