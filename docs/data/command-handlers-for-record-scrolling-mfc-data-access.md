---
title: Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 8bbacd6625e846381d2bafc8133e8b36efe51b1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213452"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Controladores de comandos para el desplazamiento por los registros (acceso a datos MFC)

La clase [CRecordView](../mfc/reference/crecordview-class.md) proporciona el control de comandos predeterminado para los siguientes comandos estándar:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

La función miembro `OnMove` proporciona el control de comandos predeterminado para los cuatro comandos, que se mueven de un registro a otro. Cuando se emiten estos comandos, RFX (o DFX) carga el nuevo registro en los campos del conjunto de registros y DDX mueve los valores a los controles del formulario de registro. Para obtener información sobre RFX, consulte [intercambio de campos de registros (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Asegúrese de utilizar estos identificadores de comando estándar para todos los objetos de interfaz de usuario asociados a los comandos estándar de exploración de registros.

## <a name="see-also"></a>Consulte también

[Admitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
