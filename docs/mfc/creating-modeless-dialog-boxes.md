---
title: Crear cuadros de diálogo no modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7da6d82257d1407dfcf4d6d3c15cdadbb8c0fa30
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685657"
---
# <a name="creating-modeless-dialog-boxes"></a>Crear cuadros de diálogo no modales

En el caso de un cuadro de diálogo no modal, debe proporcionar su propio constructor público en la clase de cuadro de diálogo. Para crear un cuadro de diálogo no modal, llame a su constructor público y, a continuación, llame a la función miembro [Create](../mfc/reference/cdialog-class.md#create) del objeto de cuadro de diálogo para cargar el recurso de cuadro de diálogo. Puede llamar a **Create** durante o después de la llamada al constructor. Si el recurso de cuadro de diálogo tiene la propiedad **WS_VISIBLE**, el cuadro de diálogo aparece inmediatamente. Si no es así, debe llamar a la función miembro [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) .

## <a name="see-also"></a>Vea también

[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)
