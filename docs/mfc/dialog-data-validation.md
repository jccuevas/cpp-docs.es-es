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
ms.openlocfilehash: 2283806d3fe7c4ff6bd3abc2ae6a86f5dd176d10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483361"
---
# <a name="dialog-data-validation"></a>Validación de datos de cuadro de diálogo

Puede especificar la validación además de intercambio de datos mediante una llamada a funciones DDV, tal como se muestra en el ejemplo de [intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md). El `DDV_MaxChars` llamada en el ejemplo valida que la cadena especificada en el control de cuadro de texto no tiene más de 20 caracteres. Normalmente, la función DDV avisa al usuario con un cuadro de mensaje si la validación se produce un error y coloca el foco en el control incorrecto por lo que el usuario puede volver a escribir los datos. Inmediatamente después de la función DDX, se debe llamar una función DDV para un control determinado para el mismo control.

También puede definir sus propias rutinas DDX y DDV personalizadas. Para obtener más información sobre este y otros aspectos de DDX y DDV, vea [Nota técnica 26](../mfc/tn026-ddx-and-ddv-routines.md).

El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) escribirá todos la DDX y DDV llama en el mapa de datos por usted.

## <a name="see-also"></a>Vea también

[Intercambio y validación de datos de cuadros de diálogo](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Intercambio de datos de cuadro de diálogo](../mfc/dialog-data-exchange.md)

