---
title: Clase CFieldExchange | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- enum FieldType, CFieldExchange
- RFX (record field exchange) [C++]
- RFX (record field exchange) [C++], classes for
- CFieldExchange class
- FieldType enumeration
- data types [C++], custom
- enum FieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 948f13dc54fcd83941bab8e63b2ab2704d84cb87
ms.lasthandoff: 02/24/2017

---
# <a name="cfieldexchange-class"></a>Clase CFieldExchange
Admite las rutinas de intercambio de campos de registro (RFX) y de intercambio masivo de campos de registro (RFX Masivo) utilizadas por las clases de base de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|Devuelve distinto de cero si la operación actual es adecuado para el tipo de campo que se está actualizando.|  
|[CFieldExchange:: SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos del conjunto de registros, columna o parámetro: representado por todas las siguientes llamadas a funciones de RFX hasta la siguiente llamada a `SetFieldType`.|  
  
## <a name="remarks"></a>Comentarios  
 `CFieldExchange`no tiene una clase base.  
  
 Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos personalizados o cuando se implementa la obtención masiva de filas; de lo contrario, no directamente utilizará esta clase. RFX y RFX masivo intercambia datos entre los miembros de datos de campo del objeto de conjunto de registros y los campos correspondientes del registro actual en el origen de datos.  
  
> [!NOTE]
>  Si trabaja con las clases de objetos de acceso a datos (DAO) en lugar de las clases de Open Database Connectivity (ODBC), utilice la clase [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) en su lugar. Para obtener más información, vea el artículo [: base de datos de información general de programación](../../data/data-access-programming-mfc-atl.md).  
  
 Un `CFieldExchange` objeto proporciona la información de contexto necesaria para que el intercambio de campos de registros o intercambio masivo de campos de registros para tomar colocar. `CFieldExchange`los objetos admiten una serie de operaciones, incluidos los parámetros de enlace y los miembros de datos y establecer varios marcadores en los campos del registro actual. Se realizan operaciones RFX y RFX masivo en miembros de datos de clase de conjunto de registros de tipos definidos por el `enum` **FieldType** en `CFieldExchange`. Posibles **FieldType** valores son:  
  
- **CFieldExchange::outputColumn** de los miembros de datos de campo.  
  
- **CFieldExchange::inputParam** o **CFieldExchange::param** para los miembros de datos de parámetro de entrada.  
  
- **CFieldExchange::outputParam** para miembros de datos del parámetro de salida.  
  
- **CFieldExchange::inoutParam** para los miembros de datos de parámetro de entrada y salida.  
  
 La mayoría de los miembros de datos y funciones de miembro de la clase se proporciona para escribir sus propias rutinas RFX personalizados. Utilizará `SetFieldType` con frecuencia. Para obtener más información, consulte los artículos [intercambio de campos de registros (RFX)](../../data/odbc/record-field-exchange-rfx.md) y [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener información sobre la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Para obtener más información acerca de las funciones globales de RFX y RFX masivo, consulte [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md) en la sección de Macros de MFC y funciones globales de esta referencia.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CFieldExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="isfieldtype"></a>CFieldExchange::IsFieldType  
 Si escribe su propia función RFX, llame a `IsFieldType` al principio de la función para determinar si puede realizar la operación actual en un tipo de miembro de datos campo o parámetro determinado (una **CFieldExchange::outputColumn**, **CFieldExchange::inputParam**, **CFieldExchange::param**, **CFieldExchange::outputParam**, o **CFieldExchange::inoutParam**).  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>Parámetros  
 *pnField*  
 En este parámetro, se devuelve el número secuencial del miembro de datos de campo o parámetro. Este número corresponde al orden del miembro de datos en el [CRecordset:: DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) (función).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación actual se puede realizar en el tipo de campo o parámetro actual.  
  
### <a name="remarks"></a>Comentarios  
 Seguir el modelo de las funciones de RFX existentes.  
  
##  <a name="setfieldtype"></a>CFieldExchange:: SetFieldType  
 Necesita una llamada a `SetFieldType` en la clase de conjunto de registros [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) invalidar.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parámetros  
 `nFieldType`  
 Un valor de la **enum FieldType**, declarados en `CFieldExchange`, que puede ser uno de los siguientes:  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>Comentarios  
 Para los miembros de datos de campo, se debe llamar a `SetFieldType` con un parámetro de **CFieldExchange::outputColumn**, seguido de las llamadas a las funciones RFX o RFX masivo. Si no ha implementado la obtención masiva de filas, ClassWizard coloca este `SetFieldType` llamar automáticamente en la sección de asignación de campo de `DoFieldExchange`.  
  
 Parametrizar la clase de conjunto de registros, debe llamar `SetFieldType` nuevo, fuera de cualquier sección de asignación de campo, seguido de llamadas RFX para todos los miembros de datos de parámetro. Cada tipo de miembro de datos de parámetro debe tener su propio `SetFieldType` llamar. La siguiente tabla distingue los distintos valores que puede pasar a `SetFieldType` para representar a los miembros de datos de parámetro de la clase:  
  
|Valor del parámetro SetFieldType|Tipo de miembro de datos de parámetro|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|Parámetro de entrada. Un valor que se pasa a la consulta del conjunto de registros o un procedimiento almacenado.|  
|**CFieldExchange::param**|Igual que **CFieldExchange::inputParam**.|  
|**CFieldExchange::outputParam**|Parámetro de salida. Procedimiento almacenado del valor devuelto es el conjunto de registros.|  
|**CFieldExchange::inoutParam**|Parámetro de entrada y salida. Procedimiento almacenado de un valor que se pasa y se devuelve desde el conjunto de registros.|  
  
 En general, cada grupo de llamadas de función RFX asociados a los miembros de datos o los miembros de datos de parámetro debe ir precedido por una llamada a `SetFieldType`. El `nFieldType` parámetro de cada `SetFieldType` llamada identifica el tipo de los miembros de datos representados por las llamadas de función RFX que sigan la `SetFieldType` llamar.  
  
 Para obtener más información sobre el control de parámetros de salida y entrada y salida, vea el `CRecordset` función miembro [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Para obtener más información acerca de las funciones RFX y RFX masivo, vea el tema [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md). Para obtener información acerca de la obtención masiva de filas, vea el artículo [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo muestra varias llamadas a funciones de RFX acompañado llamadas a `SetFieldType`. Tenga en cuenta que `SetFieldType` se llama a través de la `pFX` puntero a un `CFieldExchange` objeto.  
  
 [!code-cpp[NVC_MFCDatabase Nº&33;](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)

