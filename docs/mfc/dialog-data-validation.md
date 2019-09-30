---
title: Validación de datos de cuadro de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685765"
---
# <a name="dialog-data-validation"></a>Validación de datos de cuadro de diálogo

Puede especificar la validación además del intercambio de datos mediante una llamada a las funciones DDV, tal como se muestra en el ejemplo de [intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md). La llamada a `DDV_MaxChars` en el ejemplo valida que la cadena especificada en el control de cuadro de texto no tenga más de 20 caracteres. La función DDV normalmente avisa al usuario con un cuadro de mensaje si se produce un error en la validación y coloca el foco en el control infractor para que el usuario pueda volver a escribir los datos. Se debe llamar a una función DDV para un control determinado inmediatamente después de la función DDX para el mismo control.

También puede definir sus propias rutinas DDX y DDV personalizadas. Para obtener más información sobre este y otros aspectos de DDX y DDV, vea la [Nota técnica de MFC 26](../mfc/tn026-ddx-and-ddv-routines.md).

El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) escribirá todas las llamadas DDX y DDV en la asignación de datos.

## <a name="see-also"></a>Vea también

[Intercambio y validación de datos de cuadros de diálogo](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Trabajar con cuadros de diálogo en MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md)
