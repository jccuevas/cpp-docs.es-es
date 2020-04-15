---
title: 'Intercambio de campos de registros: Utilizar RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: dc0cdcee758f4842b0738068a8a11c4e2e404155
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367142"
---
# <a name="record-field-exchange-using-rfx"></a>Intercambio de campos de registros: Utilizar RFX

En este tema se explica lo que se hace para usar RFX en relación con lo que hace el marco de trabajo.

> [!NOTE]
> Este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) en las que no se ha implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [Conjunto de registros: obtención de registros en masa (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Los temas siguientes contienen información relacionada:

- [Intercambio](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) de campos de registros: trabajar con el código del asistente presenta los componentes principales de RFX y explica el código que el Asistente para aplicaciones MFC y **Agregar clase** (como se describe en Agregar un consumidor ODBC de [MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) escriben para admitir RFX y cómo es posible que desee modificar el código del asistente.

- Intercambio de campos de registros: el uso de las `DoFieldExchange` [funciones RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explica cómo escribir llamadas a las funciones RFX en la invalidación.

En la tabla siguiente se muestra el rol en relación con lo que el marco de trabajo hace por usted.

### <a name="using-rfx-you-and-the-framework"></a>Uso de RFX: Usted y el marco de trabajo

|Los|El marco de trabajo|
|---------|-------------------|
|Declare las clases de conjunto de registros con un asistente. Especifique los nombres y tipos de datos de los miembros de datos de campo.|El asistente deriva `CRecordset` una clase y escribe una invalidación [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) por usted, incluida una llamada de función RFX para cada miembro de datos de campo.|
|(Opcional) Agregue manualmente los miembros de datos de parámetro necesarios a la clase. Agregue manualmente una llamada de `DoFieldExchange` función RFX para cada miembro de datos de parámetro, agregue una llamada a [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) para el grupo de parámetros y especifique el número total de parámetros en [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Consulte [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Opcional) Enlazar manualmente columnas adicionales a miembros de datos de campo. Incremente manualmente [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Consulte [Conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Construir un objeto de la clase de conjunto de registros. Antes de utilizar el objeto, establezca los valores de sus miembros de datos de parámetro, si los hay.|Para mayor eficacia, el marco de trabajo enlaza previamente los parámetros mediante ODBC. Al pasar valores de parámetro, el marco de trabajo los pasa al origen de datos. Solo se envían los valores de parámetro para las consultas de requeries, a menos que las cadenas de ordenación o filtro hayan cambiado.|
|Abra un objeto de conjunto de registros mediante [CRecordset::Open](../../mfc/reference/crecordset-class.md#open).|Ejecuta la consulta del conjunto de registros, enlaza columnas a `DoFieldExchange` los miembros de datos de campo del conjunto de registros y llama para intercambiar datos entre el primer registro seleccionado y los miembros de datos de campo del conjunto de registros.|
|Desplácese por el conjunto de registros mediante [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) o un comando de menú o barra de herramientas.|Llamadas `DoFieldExchange` para transferir datos a los miembros de datos de campo desde el nuevo registro actual.|
|Agregar, actualizar y eliminar registros.|Llamadas `DoFieldExchange` para transferir datos al origen de datos.|

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Clase CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[Macros, funciones globales y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
