---
title: Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 66944221910dbd23d78a78fc951030efbee86bd0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398050"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)

El [CRecordView](../mfc/reference/crecordview-class.md) clase proporciona control para los siguientes comandos estándares de comandos predeterminado:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

El `OnMove` función miembro proporciona un comando predeterminado para los cuatro comandos de desplazamiento de los registros de control. Cuando se emiten estos comandos, RFX (o DFX) carga el nuevo registro en los campos del conjunto de registros y DDX mueve los valores a los controles del formulario de registro. Para obtener información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Asegúrese de utilizar estos identificadores de comando estándar para todos los objetos de interfaz de usuario asociados a los comandos estándar de exploración de registros.

## <a name="see-also"></a>Vea también

[Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)