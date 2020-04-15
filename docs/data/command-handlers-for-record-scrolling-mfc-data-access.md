---
title: Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 14ef845c3029f1d9a30d257f91c1b33017b6ec8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336940"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)

La clase [CRecordView](../mfc/reference/crecordview-class.md) proporciona el control de comandos predeterminado para los siguientes comandos estándar:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

La `OnMove` función miembro proporciona el control de comandos predeterminado para los cuatro comandos, que se mueven de registro a registro. Cuando se emiten estos comandos, RFX (o DFX) carga el nuevo registro en los campos del conjunto de registros y DDX mueve los valores a los controles del formulario de registro. Para obtener información acerca de RFX, vea Intercambio de campos de [registros (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
> Asegúrese de utilizar estos identificadores de comando estándar para todos los objetos de interfaz de usuario asociados a los comandos estándar de exploración de registros.

## <a name="see-also"></a>Consulte también

[Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
