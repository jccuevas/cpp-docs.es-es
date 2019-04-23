---
title: Características de las clases de vistas de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 5f8de956065571109c988bd2940d21822bba7cfd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029880"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Características de las clases de vistas de registros (acceso a datos MFC)

Puede hacer la programación de acceso a datos basada en formularios con la clase [CFormView](../mfc/reference/cformview-class.md), pero [CRecordView](../mfc/reference/crecordview-class.md) suele ser una clase mejor derivar. Además su `CFormView` características, `CRecordView`:

- Proporciona el intercambio de datos de cuadro de diálogo (DDX) entre los controles de formulario y el objeto de conjunto de registros asociado.

- Controla los comandos Mover primero, mover siguiente, mover anterior y Mover último para navegar por los registros en el objeto de conjunto de registros asociado.

- Actualiza los cambios en el registro actual cuando el usuario se mueve a otro registro.

Para obtener más información sobre la navegación, consulte [vistas de registros: Permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Vea también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)