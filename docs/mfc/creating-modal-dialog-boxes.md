---
title: Crear cuadros de diálogo Modal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fcc449a376091c07a7fb26b81fe19752bc3bcd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376649"
---
# <a name="creating-modal-dialog-boxes"></a>Crear cuadros de diálogo modales

Para crear un cuadro de diálogo modal, llame a cualquiera de los dos constructores públicos declarados en [CDialog](../mfc/reference/cdialog-class.md). A continuación, llame el objeto de cuadro de diálogo [DoModal](../mfc/reference/cdialog-class.md#domodal) función miembro para mostrar el cuadro de diálogo y administrar la interacción con él hasta que el usuario elige Aceptar o Cancelar. Esta administración por `DoModal` es lo que hace que el cuadro de diálogo modal. En los cuadros de diálogo modal, `DoModal` carga el recurso de cuadro de diálogo.

## <a name="see-also"></a>Vea también

[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

