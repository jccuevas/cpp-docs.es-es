---
title: Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c68603eff0393d76af4e0617548e5bf1dd4aa63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413697"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl

Este es un ejemplo de un uso típico de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Uso de un control de barra de estado con partes

1. Construir la `CStatusBarCtrl` objeto.

1. Llame a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) si desea establecer el alto mínimo del control de barra de estado del área de dibujo.

1. Llame a [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) para establecer el color de fondo del control de barra de estado.

1. Llame a [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) para establecer el número de elementos en un control y la coordenada del borde derecho de cada parte de la barra de estado.

1. Llame a [SetText](../mfc/reference/cstatusbarctrl-class.md#settext) para establecer el texto de una parte determinada del control de barra de estado. El mensaje invalida la parte del control que ha cambiado, lo que hace que muestra el texto nuevo cuando el control siguiente recibe el mensaje WM_PAINT.

En algunos casos, la barra de estado sólo necesita mostrar una línea de texto. En este caso, realice una llamada a [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Esto coloca el control de barra de estado en modo "simple", que muestra una sola línea de texto.

## <a name="see-also"></a>Vea también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

