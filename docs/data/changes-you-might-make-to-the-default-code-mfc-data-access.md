---
title: Posibles cambios en el código predeterminado (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: fc448ae1e13025a83b33386c2845bdf7bb4d5eec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398031"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Posibles cambios en el código predeterminado (acceso a datos MFC)

El [MFC Application Wizard](../mfc/reference/database-support-mfc-application-wizard.md) escribe una clase de conjunto de registros que selecciona todos los registros en una sola tabla. Con frecuencia, deseará modificar este comportamiento de alguna de las siguientes maneras:

- Establecer un filtro o un criterio de ordenación para el conjunto de registros. Hacer esto en `OnInitialUpdate` después de que se construye el objeto de conjunto de registros, pero antes su `Open` se llama a la función miembro. Para obtener más información, consulte [conjunto de registros: Filtrar registros (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) y [conjunto de registros: Ordenar registros (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametrice el conjunto de registros. Especifique el valor de parámetro de tiempo de ejecución real después del filtro. Para obtener más información, consulte [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Pasa una cadena SQL personalizada a la [abierto](../mfc/reference/crecordset-class.md#open) función miembro. Para obtener una explicación de lo que puede lograr con esta técnica, consulte [SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Vea también

[Uso de una vista de registros](../data/using-a-record-view-mfc-data-access.md)