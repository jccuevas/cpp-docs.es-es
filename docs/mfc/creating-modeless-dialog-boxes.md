---
title: Crear cuadros de diálogo no modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7a6125e84438b0ef2ad541c26bda33051d483c8d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619636"
---
# <a name="creating-modeless-dialog-boxes"></a>Crear cuadros de diálogo no modales

En el caso de un cuadro de diálogo no modal, debe proporcionar su propio constructor público en la clase de cuadro de diálogo. Para crear un cuadro de diálogo no modal, llame a su constructor público y, a continuación, llame a la función miembro [Create](reference/cdialog-class.md#create) del objeto de cuadro de diálogo para cargar el recurso de cuadro de diálogo. Puede llamar a **Create** durante o después de la llamada al constructor. Si el recurso de cuadro de diálogo tiene la propiedad **WS_VISIBLE**, el cuadro de diálogo aparece inmediatamente. Si no es así, debe llamar a la función miembro [ShowWindow](reference/cwnd-class.md#showwindow) .

## <a name="see-also"></a>Consulte también

[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)
