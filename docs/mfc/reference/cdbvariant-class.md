---
title: CDBVariant (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
dev_langs:
- C++
helpviewer_keywords:
- CDBVariant class
- Variant data types, ODBC
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: 21
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
ms.openlocfilehash: 930115ce4fe673e82a447ab1d90c260fe2b941d6
ms.lasthandoff: 02/24/2017

---
# <a name="cdbvariant-class"></a>CDBVariant (clase)
Representa un tipo de datos variant para las clases ODBC de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDBVariant  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDBVariant::CDBVariant](#cdbvariant)|Construye un objeto `CDBVariant`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDBVariant::Clear](#clear)|Borra la `CDBVariant` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDBVariant::m_dwType](#m_dwtype)|Contiene el tipo de datos del valor almacenado actualmente. Escriba `DWORD`.|  
  
### <a name="public-union-members"></a>Miembros públicos de unión  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDBVariant::m_boolVal](#m_boolval)|Contiene un valor de tipo **BOOL**.|  
|[CDBVariant::m_chVal](#m_chval)|Contiene un valor de tipo `unsigned char`.|  
|[CDBVariant::m_dblVal](#m_dblval)|Contiene un valor de tipo **doble**.|  
|[CDBVariant::m_fltVal](#m_fltval)|Contiene un valor de tipo **float**.|  
|[CDBVariant::m_iVal](#m_ival)|Contiene un valor de tipo **breve**.|  
|[CDBVariant::m_lVal](#m_lval)|Contiene un valor de tipo **largo**.|  
|[CDBVariant::m_pbinary](#m_pbinary)|Contiene un puntero a un objeto de tipo `CLongBinary`.|  
|[CDBVariant::m_pdate](#m_pdate)|Contiene un puntero a un objeto de tipo **TIMESTAMP_STRUCT**.|  
|[CDBVariant::m_pstring](#m_pstring)|Contiene un puntero a un objeto de tipo `CString`.|  
|[CDBVariant::m_pstringA](#m_pstringa)|Almacena un puntero a ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|  
|[CDBVariant::m_pstringW](#m_pstringw)|Almacena un puntero a una amplia [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CDBVariant`no tiene una clase base.  
  
 `CDBVariant`es similar a [COleVariant](../../mfc/reference/colevariant-class.md); sin embargo, `CDBVariant` no utiliza OLE. `CDBVariant`le permite almacenar un valor sin preocuparse por el tipo de datos. `CDBVariant`realiza un seguimiento del tipo de datos del valor actual, que se almacena en una unión.  
  
 Clase [CRecordset](../../mfc/reference/crecordset-class.md) utiliza `CDBVariant` objetos en tres funciones miembro: `GetFieldValue`, `GetBookmark`, y `SetBookmark`. Por ejemplo, `GetFieldValue` le permite capturar dinámicamente los datos de una columna. Dado que el tipo de datos de la columna no puede conocerse en tiempo de ejecución `GetFieldValue` utiliza un `CDBVariant` objeto para almacenar datos de la columna.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CDBVariant`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdb.h  
  
##  <a name="cdbvariant"></a>CDBVariant::CDBVariant  
 Crea un valor NULL `CDBVariant` objeto.  
  
```  
CDBVariant();
```  
  
### <a name="remarks"></a>Comentarios  
 Establece la [m_dwType](#m_dwtype) miembro de datos **DBVT_NULL**.  
  
##  <a name="clear"></a>CDBVariant::Clear  
 Llame a esta función miembro para borrar la `CDBVariant` objeto.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el valor de la [m_dwType](#m_dwtype) miembro de datos es **DBVT_DATE**, **DBVT_STRING**, o **DBVT_BINARY**, **borrar** libera la memoria asociada al miembro de puntero de unión. **Borrar** establece `m_dwType` a **DBVT_NULL**.  
  
 El `CDBVariant` llamadas de destructor **borrar**.  
  
##  <a name="m_boolval"></a>CDBVariant::m_boolVal  
 Almacena un valor de tipo **BOOL**.  
  
### <a name="remarks"></a>Comentarios  
 El **m_boolVal** miembro de datos pertenece a una unión. Antes de acceder a **m_boolVal**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_BOOL**, a continuación, **m_boolVal** contendrá un valor válido; en caso contrario, obtener acceso a **m_boolVal** producirá resultados poco confiables.  
  
##  <a name="m_chval"></a>CDBVariant::m_chVal  
 Almacena un valor de tipo `unsigned char`.  
  
### <a name="remarks"></a>Comentarios  
 El **m_chVal** miembro de datos pertenece a una unión. Antes de acceder a **m_chVal**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_UCHAR**, a continuación, **m_chVal** contiene un valor válido; en caso contrario, obtener acceso a **m_chVal** producirá resultados poco confiables.  
  
##  <a name="m_dblval"></a>CDBVariant::m_dblVal  
 Almacena un valor de tipo **doble**.  
  
### <a name="remarks"></a>Comentarios  
 El **m_dblVal** miembro de datos pertenece a una unión. Antes de acceder a **m_dblVal**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_DOUBLE**, a continuación, **m_dblVal** contiene un valor válido; en caso contrario, obtener acceso a **m_dblVal** producirá resultados poco confiables.  
  
##  <a name="m_dwtype"></a>CDBVariant::m_dwType  
 Este miembro de datos contiene el tipo de datos para el valor almacenado actualmente en el `CDBVariant` miembro de datos de unión del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Antes de acceder a esta unión, debe comprobar el valor de `m_dwType` para determinar qué miembro de datos de unión para tener acceso. La tabla siguiente enumeran los valores posibles de `m_dwType` y el miembro de datos de unión correspondiente.  
  
|m_dwType|Miembro de datos de unión|  
|---------------|-----------------------|  
|**DBVT_NULL**|Ningún miembro de unión es válido para el acceso.|  
|**DBVT_BOOL**|[m_boolVal](#m_boolval)|  
|**DBVT_UCHAR**|[m_chVal](#m_chval)|  
|**DBVT_SHORT**|[m_iVal](#m_ival)|  
|**DBVT_LONG**|[m_lVal](#m_lval)|  
|**DBVT_SINGLE**|[m_fltVal](#m_fltval)|  
|**DBVT_DOUBLE**|[m_dblVal](#m_dblval)|  
|**DBVT_DATE**|[m_pdate](#m_pdate)|  
|**DBVT_STRING**|[m_pstring](#m_pstring)|  
|**DBVT_BINARY**|[m_pbinary](#m_pbinary)|  
|**DBVT_ASTRING**|[m_pstringA](#m_pstringa)|  
|**DBVT_WSTRING**|[m_pstringW](#m_pstringw)|  
  
##  <a name="m_fltval"></a>CDBVariant::m_fltVal  
 Almacena un valor de tipo **float**.  
  
### <a name="remarks"></a>Comentarios  
 El **m_fltVal** miembro de datos pertenece a una unión. Antes de acceder a **m_fltVal**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_SINGLE**, a continuación, **m_fltVal** contiene un valor válido; en caso contrario, obtener acceso a **m_fltVal** producirá resultados poco confiables.  
  
##  <a name="m_ival"></a>CDBVariant::m_iVal  
 Almacena un valor de tipo **breve**.  
  
### <a name="remarks"></a>Comentarios  
 El **m_iVal** miembro de datos pertenece a una unión. Antes de acceder a **m_iVal**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_SHORT**, a continuación, **m_iVal** contiene un valor válido; en caso contrario, obtener acceso a **m_iVal** producirá resultados poco confiables.  
  
##  <a name="m_lval"></a>CDBVariant::m_lVal  
 Almacena un valor de tipo **largo**.  
  
### <a name="remarks"></a>Comentarios  
 El **m_lVal** miembro de datos pertenece a una unión. Antes de acceder a **m_lVal**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_LONG**, a continuación, **m_lVal** contiene un valor válido; en caso contrario, obtener acceso a **m_lVal** producirá resultados poco confiables.  
  
##  <a name="m_pbinary"></a>CDBVariant::m_pbinary  
 Almacena un puntero a un objeto de tipo [CLongBinary](../../mfc/reference/clongbinary-class.md).  
  
### <a name="remarks"></a>Comentarios  
 El **m_pbinary** miembro de datos pertenece a una unión. Antes de acceder a **m_pbinary**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_BINARY**, a continuación, **m_pbinary** contiene un puntero válido; en caso contrario, obtener acceso a **m_pbinary** producirá resultados poco confiables.  
  
##  <a name="m_pdate"></a>CDBVariant::m_pdate  
 Almacena un puntero a un objeto de tipo **TIMESTAMP_STRUCT**.  
  
### <a name="remarks"></a>Comentarios  
 El **m_pdate** miembro de datos pertenece a una unión. Antes de acceder a **m_pdate**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_DATE**, a continuación, **m_pdate** contiene un puntero válido; en caso contrario, obtener acceso a **m_pdate** producirá resultados poco confiables.  
  
 Para obtener más información acerca de la **TIMESTAMP_STRUCT** tipo de datos, vea el tema [tipos de datos C](https://msdn.microsoft.com/library/ms714556.aspx) en el apéndice D de la *referencia del programador de ODBC* en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="m_pstring"></a>CDBVariant::m_pstring  
 Almacena un puntero a un objeto de tipo [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Comentarios  
 El **m_pstring** miembro de datos pertenece a una unión. Antes de acceder a **m_pstring**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_STRING**, a continuación, **m_pstring** contiene un puntero válido; en caso contrario, obtener acceso a **m_pstring** producirá resultados poco confiables.  
  
##  <a name="m_pstringa"></a>CDBVariant::m_pstringA  
 Almacena un puntero a ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El **m_pstringA** miembro de datos pertenece a una unión. Antes de acceder a **m_pstringA**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_ASTRING**, a continuación, **m_pstringA** contiene un puntero válido; en caso contrario, obtener acceso a **m_pstringA** producirá resultados poco confiables.  
  
##  <a name="m_pstringw"></a>CDBVariant::m_pstringW  
 Almacena un puntero a una amplia [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El **m_pstringW** miembro de datos pertenece a una unión. Antes de acceder a **m_pstringW**, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en **DBVT_WSTRING**, a continuación, **m_pstringW** contiene un puntero válido; en caso contrario, obtener acceso a **m_pstringW** producirá resultados poco confiables.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)

