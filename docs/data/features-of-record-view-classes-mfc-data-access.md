---
title: Características de las clases de vistas de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213439"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Características de las clases de vistas de registros (acceso a datos MFC)

Puede realizar la programación de acceso a datos basada en formularios con la clase [CFormView](../mfc/reference/cformview-class.md), pero [CRecordView](../mfc/reference/crecordview-class.md) suele ser una mejor clase de la que derivar. Además de las características de `CFormView`, `CRecordView`:

- Proporciona intercambio de datos de cuadros de diálogo (DDX) entre los controles de formulario y el objeto de conjunto de registros asociado.

- Controla los comandos desplazar primero, moverse siguiente, desplazar anterior y bajar el último para navegar por los registros del objeto de conjunto de registros asociado.

- Actualiza los cambios realizados en el registro actual cuando el usuario se mueve a otro registro.

Para obtener más información sobre la navegación, consulte [vistas de registros: permitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Consulte también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)
