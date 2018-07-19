---
title: Clase CFieldExchange | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96c70bc7c6c506d033b39ca55ba2b1a090767b5d
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951692"
---
# <a name="cfieldexchange-class"></a>Clase CFieldExchange
Admite las rutinas de intercambio de campos de registro (RFX) y de intercambio masivo de campos de registro (RFX Masivo) utilizadas por las clases de base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|Devuelve distinto de cero si la operación actual no es adecuado para el tipo de campo que se está actualizando.|  
|[CFieldExchange:: SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos del conjunto de registros, columna o parámetro, representado por todas las llamadas siguientes a las funciones RFX hasta la siguiente llamada a `SetFieldType`.|  
  
## <a name="remarks"></a>Comentarios  
 `CFieldExchange` no tiene una clase base.  
  
 Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados o cuando se implementan la obtención masiva de filas; en caso contrario, no directamente usará esta clase. RFX y RFX masivo intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los campos correspondientes del registro actual en el origen de datos.  
  
> [!NOTE]
>  Si está trabajando con las clases de Data Access Objects (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) en su lugar. Para obtener más información, vea el artículo [: base de datos de información general de programación](../../data/data-access-programming-mfc-atl.md).  
  
 Un `CFieldExchange` objeto proporciona la información de contexto necesaria para que el intercambio de campos de registros o intercambio masivo de campos de registros pueda colocar. `CFieldExchange` los objetos admiten una serie de operaciones, incluidos los parámetros de enlace y los miembros de datos de campo y el establecimiento de varias marcas en los campos del registro actual. Se realizan operaciones RFX y RFX masivo en miembros de datos de la clase de conjunto de registros de tipos definidos por el **enum** **FieldType** en `CFieldExchange`. Posibles **FieldType** valores son:  
  
- **CFieldExchange::outputColumn** para los miembros de datos de campo.  
  
- **CFieldExchange::inputParam** o **CFieldExchange::param** para los miembros de datos de parámetro de entrada.  
  
- **CFieldExchange::outputParam** para los miembros de datos de parámetro de salida.  
  
- **CFieldExchange::inoutParam** para los miembros de datos de parámetro de entrada/salida.  
  
 La mayoría de los miembros de datos y funciones de miembro de la clase se proporciona para escribir sus propias rutinas RFX personalizados. Va a usar `SetFieldType` con frecuencia. Para obtener más información, vea los artículos [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md) y [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener más información acerca de las funciones globales de RFX y RFX masivo, consulte [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md) en la sección de Macros de MFC y las variables globales de esta referencia.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CFieldExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType  
 Si escribe su propia función RFX, llame a `IsFieldType` al principio de la función para determinar si se puede realizar la operación actual en un tipo de miembro de datos campo o parámetro determinado (un **CFieldExchange::outputColumn**, **CFieldExchange::inputParam**, **CFieldExchange::param**, **CFieldExchange::outputParam**, o **CFieldExchange::inoutParam** ).  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>Parámetros  
 *pnField*  
 En este parámetro, se devuelve el número secuencial del miembro de datos de campo o parámetro. Este número corresponde al orden del miembro de datos en el [CRecordset:: DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) (función).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación actual se puede realizar en el tipo de campo o parámetro actual.  
  
### <a name="remarks"></a>Comentarios  
 Sigue el modelo de las funciones RFX existentes.  
  
##  <a name="setfieldtype"></a>  CFieldExchange:: SetFieldType  
 Se necesita una llamada a `SetFieldType` en la clase de conjunto de registros [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) invalidar.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parámetros  
 *nFieldType*  
 Un valor de la **enum FieldType**, declarados en `CFieldExchange`, que puede ser uno de los siguientes:  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>Comentarios  
 Para los miembros de datos de campo, debe llamar a `SetFieldType` con un parámetro de **CFieldExchange::outputColumn**, seguido de llamadas a las funciones RFX o RFX masivo. Si no ha implementado la obtención masiva de filas, entonces ClassWizard coloca este `SetFieldType` llamar automáticamente en la sección de asignación de campo de `DoFieldExchange`.  
  
 Si parametrizar la clase de conjunto de registros, se debe llamar a `SetFieldType` nuevo, fuera de cualquier sección de asignación de campo, seguido por llamadas RFX para todos los miembros de datos de parámetro. Cada tipo de miembro de datos de parámetro debe tener su propio `SetFieldType` llamar. En la siguiente tabla distingue los distintos valores que puede pasar a `SetFieldType` para representar los miembros de datos de parámetro de la clase:  
  
|Valor del parámetro SetFieldType|Tipo de miembro de datos de parámetro|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|Parámetro de entrada. Un valor que se pasa a la consulta del conjunto de registros o un procedimiento almacenado.|  
|**CFieldExchange::param**|Igual que **CFieldExchange::inputParam**.|  
|**CFieldExchange::outputParam**|Parámetro de salida. Un valor devuelto del procedimiento almacenado del conjunto de registros.|  
|**CFieldExchange::inoutParam**|Parámetro de entrada/salida. Procedimiento almacenado de un valor que se pasó y se devuelve desde el conjunto de registros.|  
  
 En general, cada grupo de llamadas de función RFX asociadas a los miembros de datos de campo o miembros de datos de parámetro debe ir precedida de una llamada a `SetFieldType`. El *nFieldType* parámetro de cada `SetFieldType` llamada identifica el tipo de los miembros de datos representados por las llamadas de función RFX que sigan la `SetFieldType` llamar.  
  
 Para obtener más información sobre el control de parámetros de salida y entrada/salida, consulte el `CRecordset` función miembro [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Para obtener más información acerca de las funciones RFX y RFX masivo, vea el tema [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md). Para obtener información relacionada sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra varias llamadas a funciones RFX con que acompaña a llamadas a `SetFieldType`. Tenga en cuenta que `SetFieldType` se llama a través de la `pFX` puntero a un `CFieldExchange` objeto.  
  
 [!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)
