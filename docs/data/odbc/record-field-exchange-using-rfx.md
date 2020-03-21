---
title: 'Intercambio de campos de registros: Utilizar RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
ms.openlocfilehash: 70197d2a9130388e86bb94f0d670360bb35febeb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075863"
---
# <a name="record-field-exchange-using-rfx"></a>Intercambio de campos de registros: Utilizar RFX

En este tema se explica lo que se hace para usar RFX en relación con lo que hace el marco de trabajo.

> [!NOTE]
>  Este tema se aplica a las clases derivadas de [CRecordset](../../mfc/reference/crecordset-class.md) en las que no se ha implementado la obtención masiva de filas. Si usa la obtención masiva de filas, se implementará el intercambio masivo de campos de registros (RFX masivo). RFX masivo es similar a RFX. Para comprender las diferencias, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Los temas siguientes contienen información relacionada:

- [Intercambio de campos de registros: trabajar con el código del asistente](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) presenta los componentes principales de RFX y explica el código que el Asistente para aplicaciones MFC y la **clase agregar** (como se describe en [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) escriben para admitir RFX y cómo podría querer modificar el código del asistente.

- [Intercambio de campos de registros: con las funciones de RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) se explica cómo escribir llamadas a las funciones de RFX en la invalidación de `DoFieldExchange`.

En la tabla siguiente se muestra el rol con respecto a lo que hace el marco de trabajo.

### <a name="using-rfx-you-and-the-framework"></a>Usar RFX: usted y el marco de trabajo

|Los|El marco de trabajo|
|---------|-------------------|
|Declare las clases de conjunto de registros con un asistente. Especifique los nombres y los tipos de datos de los miembros de datos de campo.|El asistente deriva una `CRecordset` clase y escribe una invalidación de [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) automáticamente, incluida una llamada de función RFX para cada miembro de datos de campo.|
|Opta Agregue manualmente los miembros de datos de parámetro necesarios a la clase. Agregue manualmente una llamada de función RFX a `DoFieldExchange` por cada miembro de datos de parámetro, agregue una llamada a [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) para el grupo de parámetros y especifique el número total de parámetros en [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).||
|Opta Enlazar manualmente columnas adicionales a los miembros de datos de campo. Incrementar manualmente [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). Vea [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||
|Construya un objeto de la clase de conjunto de registros. Antes de usar el objeto, establezca los valores de sus miembros de datos de parámetro, si los hay.|Por motivos de eficacia, el marco de trabajo preenlaza los parámetros mediante ODBC. Al pasar valores de parámetro, el marco de trabajo los pasa al origen de datos. Solo se envían los valores de parámetro para las reconsultas, a menos que hayan cambiado las cadenas de filtro o de ordenación.|
|Abra un objeto de conjunto de registros mediante [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open).|Ejecuta la consulta del conjunto de registros, enlaza las columnas con los miembros de datos de campo del conjunto de registros y llama a `DoFieldExchange` para intercambiar datos entre el primer registro seleccionado y los miembros de datos de campo del conjunto de registros.|
|Desplácese por el conjunto de registros mediante [CRecordset:: Move](../../mfc/reference/crecordset-class.md#move) o un comando de menú o barra de herramientas.|Llama a `DoFieldExchange` para transferir datos a los miembros de datos de campo del nuevo registro actual.|
|Agregar, actualizar y eliminar registros.|Llama a `DoFieldExchange` para transferir datos al origen de datos.|

## <a name="see-also"></a>Consulte también

[Intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Intercambio de campos de registros: Funcionamiento de RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Conjunto de registros: Obtener cálculos SUM y otros resultados agregados (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange (clase)](../../mfc/reference/cfieldexchange-class.md)<br/>
[Macros, funciones globales y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
