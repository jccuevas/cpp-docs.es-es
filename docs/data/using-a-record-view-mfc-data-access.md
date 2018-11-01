---
title: Utilizar una vista de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: a051394fd79dfb84801a1fb9e700a7ce49ed1c7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605184"
---
# <a name="using-a-record-view--mfc-data-access"></a>Utilizar una vista de registros (acceso a datos MFC)

Este tema explica la forma habitual de personalizar el código predeterminado para vistas de registros que ha escrito por el asistente. Normalmente, desea restringir la selección de registros con un [filtro](../data/odbc/recordset-filtering-records-odbc.md) o [parámetros](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), tal vez [ordenación](../data/odbc/recordset-sorting-records-odbc.md) los registros o personalizar la instrucción SQL.

Uso de `CRecordView` es lo mismo que usar [CFormView](../mfc/reference/cformview-class.md). El enfoque básico consiste en utilizar la vista de registros para mostrar y, tal vez, actualizar los registros de un solo conjunto de registros. Más allá de eso, es posible que desee utilizar otros conjuntos de registros, como se describe en [vistas de registros: llenar un cuadro de lista de otro conjunto de registros](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>Vea también

[Vistas de registros (acceso a datos MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de controladores ODBC](../data/odbc/odbc-driver-list.md)