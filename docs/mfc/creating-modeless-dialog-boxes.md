---
title: Crear cuadros de diálogo no modal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77b80f66f2956e71b90e4d939a0fb74aef28edb1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407041"
---
# <a name="creating-modeless-dialog-boxes"></a>Crear cuadros de diálogo no modales

Para un cuadro de diálogo no modal, debe proporcionar su propio constructor público en la clase de cuadro de diálogo. Para crear un cuadro de diálogo no modal, llame a su constructor público y, a continuación, llame al objeto de cuadro de diálogo [crear](../mfc/reference/cdialog-class.md#create) función miembro para cargar el recurso de cuadro de diálogo. Puede llamar a **crear** durante o después de la llamada al constructor. Si el recurso de cuadro de diálogo tiene la propiedad **WS_VISIBLE**, el cuadro de diálogo aparece inmediatamente. Si no, debe llamar a su [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) función miembro.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

