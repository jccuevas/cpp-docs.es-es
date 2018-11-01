---
title: Características de las clases de vistas de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 2feda8f8f446e02a5056287c656707ea038f5387
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461157"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Características de las clases de vistas de registros (acceso a datos MFC)

Puede hacer la programación de acceso a datos basada en formularios con la clase [CFormView](../mfc/reference/cformview-class.md), pero [CRecordView](../mfc/reference/crecordview-class.md) suele ser una clase mejor derivar. Además su `CFormView` características, `CRecordView`:

- Proporciona el intercambio de datos de cuadro de diálogo (DDX) entre los controles de formulario y el objeto de conjunto de registros asociado.

- Controla los comandos Mover primero, mover siguiente, mover anterior y Mover último para navegar por los registros en el objeto de conjunto de registros asociado.

- Actualiza los cambios en el registro actual cuando el usuario se mueve a otro registro.

Para obtener más información sobre la navegación, consulte [vistas de registros: permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Vea también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)