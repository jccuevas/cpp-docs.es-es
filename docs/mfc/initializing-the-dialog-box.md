---
title: Inicializar el cuadro de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42526eea184cb4f28d5214fe0c56281ac6da9d6c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426112"
---
# <a name="initializing-the-dialog-box"></a>Inicializar el cuadro de diálogo

Después el cuadro de diálogo cuadro y todos sus controles se crean pero justo antes del cuadro de diálogo aparece el cuadro (de cualquier tipo) en la pantalla, el objeto de cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) se llama a la función miembro. Para un cuadro de diálogo modal, esto se produce durante el `DoModal` llamar. Para un cuadro de diálogo no modal, `OnInitDialog` se llama cuando `Create` se llama. Normalmente se reemplaza `OnInitDialog` para inicializar los controles del cuadro de diálogo, como establecer el texto inicial de un cuadro de edición. Debe llamar a la `OnInitDialog` función miembro de la clase base, `CDialog`, desde su `OnInitDialog` invalidar.

Si desea establecer el color de fondo del cuadro de diálogo (y que todos los otros cuadros de diálogo en la aplicación), consulte [establecer el Color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

