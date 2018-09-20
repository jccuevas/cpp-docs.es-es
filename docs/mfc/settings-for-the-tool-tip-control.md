---
title: Control de información sobre configuración de la herramienta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d0adfd1c7a7ae1e1f36fa8dd53610d19ad8e7b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379559"
---
# <a name="settings-for-the-tool-tip-control"></a>Configuración del control de información sobre herramientas

Puede establecer el control de información sobre herramientas ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) como activo o inactivo. Si lo establece como activo, el control de información sobre herramientas aparece cuando el cursor está sobre una herramienta. Si lo establece como inactivo, el control de información sobre herramientas no aparece cuando el cursor esté sobre una herramienta. Llame a [Activar](../mfc/reference/ctooltipctrl-class.md#activate) para activar o desactivar un control de información sobre herramientas.

Puede establecer una información sobre herramientas activa para mostrar la información sobre herramientas cuando el cursor esté sobre una herramienta, si ventana propietaria del control de información sobre herramientas está activa o inactiva, utilizando el estilo TTS_ALWAYSTIP. Si no usa este estilo, el control de información sobre herramientas aparece cuando la ventana propietaria de la herramienta está activa, pero no cuando está inactiva.

La mayoría de las aplicaciones contienen barras de herramientas con herramientas que corresponden a comandos de menú. Para estas herramientas, es conveniente que el control de información sobre herramientas muestre el mismo texto que el elemento de menú correspondiente. El sistema quita automáticamente el "y" comercial (&) caracteres del Acelerador de todas las cadenas pasa a un control de información sobre herramientas, a menos que el control tiene el estilo TTS_NOPREFIX.

## <a name="see-also"></a>Vea también

[Uso de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

