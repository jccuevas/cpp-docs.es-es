---
title: Posibles cambios en el código predeterminado (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 7ea616caf176cd1e9e2f26bee1339640067b4e3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213470"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Posibles cambios en el código predeterminado (acceso a datos MFC)

El [Asistente para aplicaciones MFC](../mfc/reference/database-support-mfc-application-wizard.md) escribe una clase de conjunto de registros que selecciona todos los registros de una sola tabla. Con frecuencia, deseará modificar este comportamiento de alguna de las siguientes maneras:

- Establecer un filtro o un criterio de ordenación para el conjunto de registros. Haga esto en `OnInitialUpdate` después de construir el objeto de conjunto de registros, pero antes de que se llame a su función miembro de `Open`. Para obtener más información, vea conjunto de registros [: filtrar registros (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) y [conjunto de registros: ordenar registros (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametrice el conjunto de registros. Especifique el valor de parámetro de tiempo de ejecución real después del filtro. Para obtener más información, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Pase una cadena SQL personalizada a la función miembro [abierta](../mfc/reference/crecordset-class.md#open) . Para obtener una explicación de lo que puede lograr con esta técnica, vea [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Consulte también

[Usar una vista de registros](../data/using-a-record-view-mfc-data-access.md)
