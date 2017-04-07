---
title: Clase CDaoFieldExchange | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- DAO (Data Access Objects), record field exchange (DFX)
- field exchange
- DFX (DAO record field exchange)
- RFX (record field exchange), DAO classes
- field exchange, record for DAO classes
- exchanging data between databases and recordsets
- DFX (DAO record field exchange), DAO Record Field Exchange
- RFX (record field exchange)
- CDaoFieldExchange class
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: 23
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
ms.openlocfilehash: 31b7121f8e93f85ed73b5d095ac0995f3ddee721
ms.lasthandoff: 02/24/2017

---
# <a name="cdaofieldexchange-class"></a>Clase CDaoFieldExchange
Admite las rutinas de intercambio de campos del registro (DFX) de DAO utilizadas por las clases de base de datos DAO.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Devuelve distinto de cero si la operación actual es adecuado para el tipo de campo que se está actualizando.|  
|[CDaoFieldExchange:: SetFieldType](#setfieldtype)|Especifica el tipo de miembro de datos del conjunto de registros, columna o parámetro: representado por todas las llamadas subsiguientes a funciones DFX hasta la siguiente llamada a `SetFieldType`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDaoFieldExchange:: M_noperation](#m_noperation)|La operación de DFX que está realizarla la llamada actual al conjunto de registros `DoFieldExchange` función miembro.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Un puntero al conjunto de registros en qué DFX se están realizando operaciones.|  
  
## <a name="remarks"></a>Comentarios  
 `CDaoFieldExchange`no tiene una clase base.  
  
 Utilice esta clase si está escribiendo rutinas de intercambio de datos para tipos de datos; de lo contrario, no directamente utilizará esta clase. DFX intercambia datos entre los miembros de datos de campo de la [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto y los campos correspondientes del registro actual en el origen de datos. DFX gestiona el intercambio en ambas direcciones, desde el origen de datos y al origen de datos. Consulte [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) para obtener información acerca de cómo escribir rutinas DFX.  
  
> [!NOTE]
>  Las clases de base de datos DAO son distintas de las clases de base de datos MFC basadas en Open Database Connectivity (ODBC). Todos los nombres de clase de base de datos DAO tienen el prefijo "CDao". Aún puede acceso a orígenes de datos ODBC con las clases DAO. En general, las clases MFC basadas en DAO son más eficaces que las clases MFC basadas en ODBC. Las clases basadas en DAO pueden tener acceso a datos, incluidos los controladores ODBC, mediante su propio motor de base de datos. También admiten operaciones de lenguaje de definición de datos (DDL), como agregar tablas a través de las clases en lugar de tener que llamar a DAO.  
  
> [!NOTE]
>  Intercambio de campos de registros DAO (DFX) es muy similar al intercambio de campos de registros (RFX) en las clases de base de datos MFC basadas en ODBC ( `CDatabase`, `CRecordset`). Si conoce RFX, le resultará fácil de utilizar DFX.  
  
 Un `CDaoFieldExchange` objeto proporciona la información de contexto necesaria para DAO grabar el intercambio de campos para que se realice. `CDaoFieldExchange`los objetos admiten una serie de operaciones, incluidos los parámetros de enlace y los miembros de datos y establecer varios marcadores en los campos del registro actual. Operaciones DFX se realizan en los miembros de datos de clase de conjunto de registros de tipos definidos por el `enum` **FieldType** en `CDaoFieldExchange`. Posibles **FieldType** valores son:  
  
- **CDaoFieldExchange:: outputColumn** de los miembros de datos de campo.  
  
- **CDaoFieldExchange:: param** para los miembros de datos de parámetro.  
  
 El [IsValidOperation](#isvalidoperation) se proporciona una función de miembro para escribir sus propias rutinas DFX personalizadas. Va a usar [SetFieldType](#setfieldtype) con frecuencia en su [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funciones. Para obtener más información acerca de las funciones globales DFX, vea [funciones de intercambio de campos de registros](../../mfc/reference/record-field-exchange-functions.md). Para obtener información acerca de cómo escribir rutinas DFX para sus propios tipos de datos, consulte [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdao.h  
  
##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation  
 Si escribe su propia función DFX, llame a `IsValidOperation` al principio de la función para determinar si se puede realizar la operación actual en un tipo de miembro de datos de campo determinado (una **CDaoFieldExchange:: outputColumn** o un **CDaoFieldExchange:: param**).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación actual es adecuada para el tipo de campo que se va a actualizar.  
  
### <a name="remarks"></a>Comentarios  
 Algunas de las operaciones realizadas por el mecanismo DFX se aplican sólo a uno de los tipos de campo posibles. Seguir el modelo de las funciones existentes.  
  
 Para obtener información adicional acerca de cómo escribir rutinas DFX personalizadas, consulte [Nota técnica 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>CDaoFieldExchange:: M_noperation  
 Identifica la operación que se realizará en el [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto asociado con el objeto de exchange del campo.  
  
### <a name="remarks"></a>Comentarios  
 La `CDaoFieldExchange` objeto proporciona el contexto para un número de operaciones DFX diferentes en el conjunto de registros.  
  
> [!NOTE]
>  El **PSEUDONULL** valor descrito en las operaciones de MarkForAddNew y SetFieldNull es un valor que se utiliza para marcar campos Null. El mecanismo de intercambio de campos de registros DAO (DFX) utiliza este valor para determinar qué campos se han marcado explícitamente Null. **PSEUDONULL** no es necesario para [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) y [COleCurrency](../../mfc/reference/colecurrency-class.md) campos.  
  
 Los valores posibles de **m_nOperation** son:  
  
|Operación|Descripción|  
|---------------|-----------------|  
|**AddToParameterList**|Compila el **parámetros** cláusula de la instrucción SQL.|  
|**AddToSelectList**|Compila el **seleccione** cláusula de la instrucción SQL.|  
|**BindField**|Enlaza un campo de la base de datos a una ubicación de memoria de la aplicación.|  
|**BindParam**|Establece los valores de parámetro para la consulta.|  
|**Corrección**|Establece el estado Null para un campo.|  
|**AllocCache**|Asigna la memoria caché utilizada para buscar campos "sucio" en el conjunto de registros.|  
|**StoreField**|Guarda el registro actual en la memoria caché.|  
|**LoadField**|Restablece las variables de miembro de datos en caché en el conjunto de registros.|  
|**FreeCache**|Libera la memoria caché utilizada para buscar campos "sucio" en el conjunto de registros.|  
|`SetFieldNull`|Estado de un campo se establece en Null y el valor a **PSEUDONULL**.|  
|**MarkForAddNew**|Marca los campos "sucio" Si no **PSEUDONULL**.|  
|**MarkForEdit**|Marca los campos "sucio" Si no coinciden con la memoria caché.|  
|**SetDirtyField**|Establece los campos valores marcados como "sucio."|  
|**DumpField**|Vuelca el contenido de un campo (sólo debug).|  
|**MaxDFXOperation**|Se utiliza para comprobar la entrada.|  
  
##  <a name="m_prs"></a>CDaoFieldExchange::m_prs  
 Contiene un puntero a la [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objeto asociado a la `CDaoFieldExchange` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setfieldtype"></a>CDaoFieldExchange:: SetFieldType  
 Llame a `SetFieldType` en su `CDaoRecordset` clase `DoFieldExchange` invalidar.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parámetros  
 `nFieldType`  
 Un valor de la **enum FieldType**, declarados en `CDaoFieldExchange`, que puede ser cualquiera de las siguientes acciones:  
  
- **CDaoFieldExchange:: outputColumn**  
  
- **CDaoFieldExchange:: param**  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, ClassWizard escribe esta llamada. Si escribir su propia función y está utilizando el Asistente para escribir su `DoFieldExchange` función, agregue llamadas a su propia función fuera de la asignación de campo. Si no utiliza al asistente, no habrá una asignación de campo. La llamada precede a llamadas a funciones DFX, uno para cada miembro de datos de campo de la clase e identifica el tipo de campo como **CDaoFieldExchange:: outputColumn**.  
  
 Si parametrizar la clase de conjunto de registros, debe agregar llamadas a DFX para todos los miembros de datos de parámetro (fuera de la asignación de campo) y preceder a estas llamadas con una llamada a `SetFieldType`. Pasar el valor **CDaoFieldExchange:: param**. (En su lugar, puede usar un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y establecer sus valores de parámetro.)  
  
 En general, cada grupo de llamadas a funciones DFX asociados a los miembros de datos o los miembros de datos de parámetro debe ir precedido por una llamada a `SetFieldType`. El `nFieldType` parámetro de cada `SetFieldType` llamada identifica el tipo de los miembros de datos representados por las llamadas a funciones DFX que sigan la `SetFieldType` llamar.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (clase)](../../mfc/reference/cdaorecordset-class.md)

