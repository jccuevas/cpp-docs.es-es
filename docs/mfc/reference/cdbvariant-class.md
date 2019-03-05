---
title: CDBVariant (clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 41ea20bcddc53142773d474af41021e9c71af1aa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289877"
---
# <a name="cdbvariant-class"></a>CDBVariant (clase)

Representa un tipo de datos variant para las clases ODBC de MFC.

## <a name="syntax"></a>Sintaxis

```
class CDBVariant
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Construye un objeto `CDBVariant`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDBVariant::Clear](#clear)|Borra la `CDBVariant` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Contiene el tipo de datos del valor almacenado actualmente. Escriba `DWORD`.|

### <a name="public-union-members"></a>Miembros públicos de unión

|nombre|Descripción|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Contiene un valor de tipo **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Contiene un valor de tipo **unsigned char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Contiene un valor de tipo **doble**.|
|[CDBVariant::m_fltVal](#m_fltval)|Contiene un valor de tipo **float**.|
|[CDBVariant::m_iVal](#m_ival)|Contiene un valor de tipo **corto**.|
|[CDBVariant::m_lVal](#m_lval)|Contiene un valor de tipo **largo**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Contiene un puntero a un objeto de tipo `CLongBinary`.|
|[CDBVariant::m_pdate](#m_pdate)|Contiene un puntero a un objeto de tipo **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Contiene un puntero a un objeto de tipo `CString`.|
|[CDBVariant::m_pstringA](#m_pstringa)|Almacena un puntero a ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|
|[CDBVariant::m_pstringW](#m_pstringw)|Almacena un puntero a una amplia [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|

## <a name="remarks"></a>Comentarios

`CDBVariant` no tiene una clase base.

`CDBVariant` es similar a [COleVariant](../../mfc/reference/colevariant-class.md); sin embargo, `CDBVariant` no utiliza OLE. `CDBVariant` le permite almacenar un valor sin preocuparse sobre el tipo de datos del valor. `CDBVariant` realiza un seguimiento del tipo de datos del valor actual, que se almacena en una unión.

Clase [CRecordset](../../mfc/reference/crecordset-class.md) utiliza `CDBVariant` objetos en tres funciones miembro: `GetFieldValue`, `GetBookmark`, y `SetBookmark`. Por ejemplo, `GetFieldValue` permite capturar dinámicamente los datos de una columna. Dado que el tipo de datos de la columna no puede conocerse en tiempo de ejecución `GetFieldValue` usa un `CDBVariant` objeto para almacenar datos de la columna.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDBVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant

Crea un valor NULL `CDBVariant` objeto.

```
CDBVariant();
```

### <a name="remarks"></a>Comentarios

Establece el [m_dwType](#m_dwtype) DBVT_NULL miembro de datos.

##  <a name="clear"></a>  CDBVariant::Clear

Llame a esta función miembro para borrar el `CDBVariant` objeto.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

Si el valor de la [m_dwType](#m_dwtype) miembro de datos es DBVT_DATE, DBVT_STRING o DBVT_BINARY, `Clear` libera la memoria asociada con el miembro de puntero de unión. `Clear` establece `m_dwType` a DBVT_NULL.

El `CDBVariant` llamadas de destructor `Clear`.

##  <a name="m_boolval"></a>  CDBVariant::m_boolVal

Almacena un valor de tipo BOOL.

### <a name="remarks"></a>Comentarios

El `m_boolVal` miembro de datos pertenece a una unión. Antes de acceder a `m_boolVal`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_BOOL, a continuación, `m_boolVal` contendrá un valor válido; en caso contrario, obtener acceso a `m_boolVal` producirá resultados no confiables.

##  <a name="m_chval"></a>  CDBVariant::m_chVal

Almacena un valor de tipo **unsigned char**.

### <a name="remarks"></a>Comentarios

El `m_chVal` miembro de datos pertenece a una unión. Antes de acceder a `m_chVal`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_UCHAR, a continuación, `m_chVal` contiene un valor válido; en caso contrario, obtener acceso a `m_chVal` producirá resultados no confiables.

##  <a name="m_dblval"></a>  CDBVariant::m_dblVal

Almacena un valor de tipo **doble**.

### <a name="remarks"></a>Comentarios

El `m_dblVal` miembro de datos pertenece a una unión. Antes de acceder a `m_dblVal`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_DOUBLE, a continuación, `m_dblVal` contiene un valor válido; en caso contrario, obtener acceso a `m_dblVal` producirá resultados no confiables.

##  <a name="m_dwtype"></a>  CDBVariant::m_dwType

Este miembro de datos contiene el tipo de datos para el valor almacenado actualmente en el `CDBVariant` miembro de datos de unión del objeto.

### <a name="remarks"></a>Comentarios

Antes de acceder a esta unión, se debe comprobar el valor de `m_dwType` con el fin de determinar qué miembro de datos de unión para tener acceso a. La tabla siguiente enumeran los valores posibles para `m_dwType` y el miembro de datos de unión correspondiente.

|m_dwType|Miembro de datos de unión|
|---------------|-----------------------|
|DBVT_NULL|No es válido para el acceso a ningún miembro de unión.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

##  <a name="m_fltval"></a>  CDBVariant::m_fltVal

Almacena un valor de tipo **float**.

### <a name="remarks"></a>Comentarios

El `m_fltVal` miembro de datos pertenece a una unión. Antes de acceder a `m_fltVal`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_SINGLE, a continuación, `m_fltVal` contiene un valor válido; en caso contrario, obtener acceso a `m_fltVal` producirá resultados no confiables.

##  <a name="m_ival"></a>  CDBVariant::m_iVal

Almacena un valor de tipo **corto**.

### <a name="remarks"></a>Comentarios

El `m_iVal` miembro de datos pertenece a una unión. Antes de acceder a `m_iVal`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_SHORT, a continuación, `m_iVal` contiene un valor válido; en caso contrario, obtener acceso a `m_iVal` producirá resultados no confiables.

##  <a name="m_lval"></a>  CDBVariant::m_lVal

Almacena un valor de tipo **largo**.

### <a name="remarks"></a>Comentarios

El `m_lVal` miembro de datos pertenece a una unión. Antes de acceder a `m_lVal`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_LONG, a continuación, `m_lVal` contiene un valor válido; en caso contrario, obtener acceso a `m_lVal` producirá resultados no confiables.

##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary

Almacena un puntero a un objeto de tipo [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Comentarios

El `m_pbinary` miembro de datos pertenece a una unión. Antes de acceder a `m_pbinary`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_BINARY, a continuación, `m_pbinary` contiene un puntero válido; en caso contrario, obtener acceso a `m_pbinary` producirá resultados no confiables.

##  <a name="m_pdate"></a>  CDBVariant::m_pdate

Almacena un puntero a un objeto de tipo TIMESTAMP_STRUCT.

### <a name="remarks"></a>Comentarios

El `m_pdate` miembro de datos pertenece a una unión. Antes de acceder a `m_pdate`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_DATE, a continuación, `m_pdate` contiene un puntero válido; en caso contrario, obtener acceso a `m_pdate` producirá resultados no confiables.

Para obtener más información sobre el tipo de datos TIMESTAMP_STRUCT, vea el tema [tipos de datos C](/previous-versions/windows/desktop/ms714556) en el apéndice D de la *referencia del programador de ODBC* en el SDK de Windows.

##  <a name="m_pstring"></a>  CDBVariant::m_pstring

Almacena un puntero a un objeto de tipo [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Comentarios

El `m_pstring` miembro de datos pertenece a una unión. Antes de acceder a `m_pstring`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_STRING, a continuación, `m_pstring` contiene un puntero válido; en caso contrario, obtener acceso a `m_pstring` producirá resultados no confiables.

##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA

Almacena un puntero a ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.

### <a name="remarks"></a>Comentarios

El `m_pstringA` miembro de datos pertenece a una unión. Antes de acceder a `m_pstringA`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_ASTRING, a continuación, `m_pstringA` contiene un puntero válido; en caso contrario, obtener acceso a `m_pstringA` producirá resultados no confiables.

##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW

Almacena un puntero a una amplia [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.

### <a name="remarks"></a>Comentarios

El `m_pstringW` miembro de datos pertenece a una unión. Antes de acceder a `m_pstringW`, compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` está establecido en DBVT_WSTRING, a continuación, `m_pstringW` contiene un puntero válido; en caso contrario, obtener acceso a `m_pstringW` producirá resultados no confiables.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
