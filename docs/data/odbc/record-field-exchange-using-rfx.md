---
title: 'Intercambio de campos de registros: Utilizar RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 8d8ba1e66c1ffc46429b5c0e987be833aef2e72f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328543"
---
# <a name="record-field-exchange-using-rfx"></a>Intercambio de campos de registros: Utilizar RFX

En este tema se explica qué hacer para utilizar RFX en función de lo que hace el marco de trabajo.

> [!NOTE]
>  En este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) en qué fila de forma masiva captura no se ha implementado. Si usas la obtención masiva de filas, se implementa el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, consulte [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Los temas siguientes contienen información relacionada:

- [Intercambio de campos de registros: Trabajar con el código de asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) presenta los principales componentes de RFX y explica el código que el Asistente para aplicaciones MFC y **Agregar clase** (como se describe en [agregar un consumidor ODBC de MFC ](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) para la compatibilidad con RFX y cómo desea modificar el código del asistente.

- [Intercambio de campos de registros: Utilizar las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) explica cómo escribir llamadas a las funciones RFX en su `DoFieldExchange` invalidar.

En la tabla siguiente se muestra su rol en relación con lo que hace el marco de trabajo para usted.

### <a name="using-rfx-you-and-the-framework"></a>Usar RFX: El programador y el marco de trabajo

|El programador|El marco de trabajo|
|---------|-------------------|
|Declare las clases de conjunto de registros con un asistente. Especifique los nombres y tipos de datos de miembros de datos de campo.|El asistente se deriva un `CRecordset` clase y escrituras un [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) invalidar para usted, incluido un RFX función llamada para cada miembro de datos de campo.|
|(Opcional) Agregue manualmente los miembros de datos de parámetro necesarios a la clase. Agregar manualmente una llamada de función RFX a `DoFieldExchange` para cada miembro de datos de parámetro, agregue una llamada a [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) para el grupo de parámetros y especifique el número total de parámetros en [m_nParams ](../../mfc/reference/crecordset-class.md#m_nparams). Consulte [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|(Opcional) Enlazar manualmente columnas adicionales a los miembros de datos de campo. Incrementar manualmente [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Consulte [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Construya un objeto de la clase de conjunto de registros. Antes de usar el objeto, establezca los valores de su parámetro miembros de datos, si existe.|Para mejorar la eficacia, el marco de trabajo prebinds los parámetros, mediante ODBC. Al pasar los valores de parámetro, el marco de trabajo pasa al origen de datos. Los valores de parámetro solo se envían nuevas consultas, a menos que se han cambiado las cadenas de ordenación o filtro.|
|Abrir un objeto de conjunto de registros mediante [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open).|Ejecuta la consulta del conjunto de registros, enlaza las columnas a los miembros de datos de campo del conjunto de registros y las llamadas `DoFieldExchange` para intercambiar datos entre el primer registro seleccionado y los miembros de datos de campo del conjunto de registros.|
|Desplazamiento en el conjunto de registros mediante [CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) o un comando de menú o barra de herramientas.|Las llamadas `DoFieldExchange` para transferir datos a los miembros de datos de campo desde el nuevo registro actual.|
|Agregar, actualizar y eliminar registros.|Las llamadas `DoFieldExchange` para transferir datos al origen de datos.|

## <a name="see-also"></a>Vea también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)<br/>
[Macros, funciones globales y Variables globales](../../mfc/reference/mfc-macros-and-globals.md)

