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
ms.openlocfilehash: 99540214d1b903c66d350145c08ab657d12ef8f7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616753"
---
# <a name="dialog-data-validation"></a>Validación de datos de cuadro de diálogo

Puede especificar la validación además del intercambio de datos mediante una llamada a las funciones DDV, tal como se muestra en el ejemplo de [intercambio de datos de cuadro de diálogo](dialog-data-exchange.md). La `DDV_MaxChars` llamada en el ejemplo valida que la cadena especificada en el control de cuadro de texto no tenga más de 20 caracteres. La función DDV normalmente avisa al usuario con un cuadro de mensaje si se produce un error en la validación y coloca el foco en el control infractor para que el usuario pueda volver a escribir los datos. Se debe llamar a una función DDV para un control determinado inmediatamente después de la función DDX para el mismo control.

También puede definir sus propias rutinas DDX y DDV personalizadas. Para obtener más información sobre este y otros aspectos de DDX y DDV, vea la [Nota técnica de MFC 26](tn026-ddx-and-ddv-routines.md).

El [Asistente para agregar variables miembro](../ide/add-member-variable-wizard.md) escribirá todas las llamadas DDX y DDV en la asignación de datos.

## <a name="see-also"></a>Consulte también

[Intercambio y validación de datos de cuadros de diálogo](dialog-data-exchange-and-validation.md)<br/>
[Trabajar con cuadros de diálogo en MFC](life-cycle-of-a-dialog-box.md)<br/>
[Intercambio de datos de cuadro de diálogo](dialog-data-exchange.md)
