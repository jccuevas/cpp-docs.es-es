---
title: CDaoFieldExchange (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5f4de25c0ed4643f93626f92a83942c70dfce5
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337845"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange (clase)
Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Devuelve distinto de cero si la operación actual es adecuado para el tipo de campo que se está actualizando.|  
|[CDaoFieldExchange:: SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos del conjunto de registros, columna o parámetro, representado por todas las llamadas subsiguientes a las funciones DFX hasta la siguiente llamada a `SetFieldType`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDaoFieldExchange:: M_noperation](#m_noperation)|La operación de DFX que está realizarla la llamada actual al conjunto de registros `DoFieldExchange` función miembro.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Un puntero al conjunto de registros en qué DFX se están realizando operaciones.|  
  
## <a name="remarks"></a>Comentarios  
 `CDaoFieldExchange` no tiene una clase base.  
  
 Utilice esta clase si va a escribir rutinas de intercambio de datos para tipos de datos personalizados; en caso contrario, no directamente usará esta clase. DFX intercambia datos entre los miembros de datos de campo de su [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto y los campos correspondientes del registro actual en el origen de datos. DFX administra el intercambio en ambas direcciones, desde el origen de datos y al origen de datos. Consulte [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) para obtener información sobre cómo escribir rutinas DFX personalizadas.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Todavía puede acceso a orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más eficaces que las clases MFC basadas en ODBC. Las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, a través de su propio motor de base de datos. También admiten las operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases en lugar de tener que llamar a DAO.  
  
> [!NOTE]
>  Intercambio de campos de registros DAO (DFX) es muy similar al intercambio de campos de registros (RFX) en las clases de base de datos MFC basadas en ODBC ( `CDatabase`, `CRecordset`). Si comprende RFX, le resultará fácil de utilizar DFX.  
  
 Un `CDaoFieldExchange` objeto proporciona la información de contexto necesaria para DAO grabar el intercambio de campos que se realice. `CDaoFieldExchange` los objetos admiten un número de operaciones, incluidos los parámetros de enlace y los miembros de datos y establecer diversas marcas en los campos del registro actual. Las operaciones de DFX se realizan en los miembros de datos de clase de conjunto de registros de tipos definidos por el **enum** **FieldType** en `CDaoFieldExchange`. Posible **FieldType** los valores son:  
  
- `CDaoFieldExchange::outputColumn` para los miembros de datos de campo.  
  
- `CDaoFieldExchange::param` para los miembros de datos de parámetro.  
  
 El [IsValidOperation](#isvalidoperation) se proporciona la función miembro para escribir sus propias rutinas DFX personalizadas. Va a usar [SetFieldType](#setfieldtype) con frecuencia en su [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funciones. Para obtener más información sobre las funciones de DFX globales, consulte [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md). Para obtener información sobre cómo escribir rutinas DFX personalizadas para sus propios tipos de datos, vea [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation  
 Si escribe su propia función DFX, llame a `IsValidOperation` al principio de la función para determinar si se puede realizar la operación actual en un tipo de miembro de datos de campo concreto (un `CDaoFieldExchange::outputColumn` o `CDaoFieldExchange::param`).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la operación actual es adecuada para el tipo de campo que se está actualizando.  
  
### <a name="remarks"></a>Comentarios  
 Algunas de las operaciones realizadas por el mecanismo DFX se aplican solo a uno de los tipos de campo posibles. Siga el modelo de las funciones DFX existentes.  
  
 Para obtener más información sobre cómo escribir rutinas DFX personalizadas, vea [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>  CDaoFieldExchange:: M_noperation  
 Identifica la operación que se realizará en el [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto asociado con el objeto de campo de exchange.  
  
### <a name="remarks"></a>Comentarios  
 La `CDaoFieldExchange` objeto que proporciona el contexto para un número de operaciones de DFX diferentes en el conjunto de registros.  
  
> [!NOTE]
>  El valor PSEUDONULL descrito en las operaciones de MarkForAddNew y SetFieldNull es un valor que se utiliza para marcar campos Null. El mecanismo de intercambio de campos de registros DAO (DFX) usa este valor para determinar qué campos se han marcado explícitamente Null. No es necesario para PSEUDONULL [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) y [COleCurrency](../../mfc/reference/colecurrency-class.md) campos.  
  
 Los valores posibles de `m_nOperation` son:  
  
|Operación|Descripción|  
|---------------|-----------------|  
|`AddToParameterList`|Compila el **parámetros** cláusula de la instrucción SQL.|  
|`AddToSelectList`|Compila el **seleccione** cláusula de la instrucción SQL.|  
|`BindField`|Enlaza un campo en la base de datos a una ubicación de memoria en la aplicación.|  
|`BindParam`|Establece los valores de parámetro de consulta del conjunto de registros.|  
|`Fixup`|Establece el estado Null para un campo.|  
|`AllocCache`|Asigna la memoria caché que se usa para comprobar los campos "sucios" en el conjunto de registros.|  
|`StoreField`|Guarda el registro actual en la memoria caché.|  
|`LoadField`|Restaura las variables de miembro de datos almacenados en caché en el conjunto de registros.|  
|`FreeCache`|Libera la memoria caché que se usa para comprobar los campos "sucios" en el conjunto de registros.|  
|`SetFieldNull`|Establece el estado de un campo Null y el valor en PSEUDONULL.|  
|`MarkForAddNew`|Campos de marcas "sucio" Si no PSEUDONULL.|  
|`MarkForEdit`|Marca los campos "sucio" Si no coinciden con la memoria caché.|  
|`SetDirtyField`|Campo de conjuntos de valores marcados como "sucio".|  
|`DumpField`|Vuelca el contenido de un campo (sólo debug).|  
|`MaxDFXOperation`|Se usa para comprobar la entrada.|  
  
##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs  
 Contiene un puntero a la [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto asociado con el `CDaoFieldExchange` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setfieldtype"></a>  CDaoFieldExchange:: SetFieldType  
 Llame a `SetFieldType` en su `CDaoRecordset` la clase `DoFieldExchange` invalidar.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parámetros  
 *nFieldType*  
 Un valor de la **enum FieldType**, declarado en `CDaoFieldExchange`, que puede ser cualquiera de las siguientes acciones:  
  
- `CDaoFieldExchange::outputColumn`  
  
- `CDaoFieldExchange::param`  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, ClassWizard escribe esta llamada para usted. Si escribir su propia función y usa el Asistente para escribir su `DoFieldExchange` de función, agregue llamadas a su propia función fuera de la asignación de campo. Si no utiliza al asistente, no habrá una asignación de campo. La llamada anterior a las llamadas a funciones DFX, uno para cada miembro de datos de campo de la clase e identifica el tipo de campo como `CDaoFieldExchange::outputColumn`.  
  
 Si parametrizar la clase de conjunto de registros, debe agregar llamadas DFX para todos los miembros de datos de parámetro (fuera de la asignación de campo) y preceder a estas llamadas con una llamada a `SetFieldType`. Pase el valor `CDaoFieldExchange::param`. (En su lugar, puede usar un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y establecer sus valores de parámetro.)  
  
 En general, cada grupo de llamadas a funciones DFX asociados a los miembros de datos o los miembros de datos de parámetro debe ir precedido por una llamada a `SetFieldType`. El *nFieldType* parámetro de cada `SetFieldType` llamada identifica el tipo de los miembros de datos representados por las llamadas a funciones DFX que siguen el `SetFieldType` llamar.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)
