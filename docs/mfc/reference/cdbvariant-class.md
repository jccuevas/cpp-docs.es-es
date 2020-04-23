---
title: Clase CDBVariant
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
ms.openlocfilehash: 9bb70acb43f2e73ade86b753ebbb7949759ce88d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754600"
---
# <a name="cdbvariant-class"></a>Clase CDBVariant

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
|[CDBVariant::Clear](#clear)|Borra el `CDBVariant` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Contiene el tipo de datos del valor almacenado actualmente. Escriba `DWORD`.|

### <a name="public-union-members"></a>Miembros de la Unión Pública

|Nombre|Descripción|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Contiene un valor de tipo **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Contiene un valor de tipo **unsigned char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Contiene un valor de tipo **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Contiene un valor de tipo **float**.|
|[CDBVariant::m_iVal](#m_ival)|Contiene un valor de tipo **short**.|
|[CDBVariant::m_lVal](#m_lval)|Contiene un valor de tipo **long**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Contiene un puntero a `CLongBinary`un objeto de tipo .|
|[CDBVariant::m_pdate](#m_pdate)|Contiene un puntero a un objeto de tipo **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Contiene un puntero a `CString`un objeto de tipo .|
|[CDBVariant::m_pstringA](#m_pstringa)|Almacena un puntero a un ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|
|[CDBVariant::m_pstringW](#m_pstringw)|Almacena un puntero a un amplio [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|

## <a name="remarks"></a>Observaciones

`CDBVariant`no tiene una clase base.

`CDBVariant`es similar a [COleVariant](../../mfc/reference/colevariant-class.md); sin `CDBVariant` embargo, no utiliza OLE. `CDBVariant`le permite almacenar un valor sin preocuparse por el tipo de datos del valor. `CDBVariant`realiza un seguimiento del tipo de datos del valor actual, que se almacena en una unión.

La clase [CRecordset](../../mfc/reference/crecordset-class.md) utiliza objetos `GetBookmark`en `SetBookmark`tres funciones `CDBVariant` miembro: `GetFieldValue`, , y . Por ejemplo, `GetFieldValue` permite capturar datos dinámicamente en una columna. Dado que es posible que el tipo de `GetFieldValue` datos `CDBVariant` de la columna no se conozca en tiempo de ejecución, usa un objeto para almacenar los datos de la columna.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CDBVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant::CDBVariant

Crea un `CDBVariant` objeto NULL.

```
CDBVariant();
```

### <a name="remarks"></a>Observaciones

Establece [el](#m_dwtype) m_dwType miembro de datos en DBVT_NULL.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant::Clear

Llame a esta función miembro para borrar el `CDBVariant` objeto.

```cpp
void Clear();
```

### <a name="remarks"></a>Observaciones

Si el valor del miembro de datos [m_dwType](#m_dwtype) `Clear` es DBVT_DATE, DBVT_STRING o DBVT_BINARY, libera la memoria asociada al miembro del puntero de unión. `Clear`se `m_dwType` establece en DBVT_NULL.

El `CDBVariant` destructor `Clear`llama .

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant::m_boolVal

Almacena un valor de tipo BOOL.

### <a name="remarks"></a>Observaciones

El `m_boolVal` miembro de datos pertenece a una unión. Antes `m_boolVal`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_boolVal` DBVT_BOOL, contendrá un valor válido; de lo `m_boolVal` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant::m_chVal

Almacena un valor de tipo **unsigned char**.

### <a name="remarks"></a>Observaciones

El `m_chVal` miembro de datos pertenece a una unión. Antes `m_chVal`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_chVal` DBVT_UCHAR, contiene un valor válido; de lo `m_chVal` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant::m_dblVal

Almacena un valor de tipo **double**.

### <a name="remarks"></a>Observaciones

El `m_dblVal` miembro de datos pertenece a una unión. Antes `m_dblVal`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_dblVal` DBVT_DOUBLE, contiene un valor válido; de lo `m_dblVal` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant::m_dwType

Este miembro de datos contiene el tipo de `CDBVariant` datos para el valor que se almacena actualmente en el miembro de datos de unión del objeto.

### <a name="remarks"></a>Observaciones

Antes de acceder a esta unión, debe comprobar el valor de `m_dwType` para determinar a qué miembro de datos de unión acceder. En la tabla siguiente `m_dwType` se enumeran los valores posibles para y el miembro de datos de unión correspondiente.

|m_dwType|Miembro de datos de la Unión|
|---------------|-----------------------|
|DBVT_NULL|Ningún miembro del sindicato es válido para el acceso.|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant::m_fltVal

Almacena un valor de tipo **float**.

### <a name="remarks"></a>Observaciones

El `m_fltVal` miembro de datos pertenece a una unión. Antes `m_fltVal`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_fltVal` DBVT_SINGLE, contiene un valor válido; de lo `m_fltVal` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant::m_iVal

Almacena un valor de tipo **short**.

### <a name="remarks"></a>Observaciones

El `m_iVal` miembro de datos pertenece a una unión. Antes `m_iVal`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_iVal` DBVT_SHORT, contiene un valor válido; de lo `m_iVal` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant::m_lVal

Almacena un valor de tipo **long**.

### <a name="remarks"></a>Observaciones

El `m_lVal` miembro de datos pertenece a una unión. Antes `m_lVal`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_lVal` DBVT_LONG, contiene un valor válido; de lo `m_lVal` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant::m_pbinary

Almacena un puntero a un objeto de tipo [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Observaciones

El `m_pbinary` miembro de datos pertenece a una unión. Antes `m_pbinary`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_pbinary` DBVT_BINARY, contiene un puntero válido; de lo `m_pbinary` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant::m_pdate

Almacena un puntero a un objeto de tipo TIMESTAMP_STRUCT.

### <a name="remarks"></a>Observaciones

El `m_pdate` miembro de datos pertenece a una unión. Antes `m_pdate`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_pdate` DBVT_DATE, contiene un puntero válido; de lo `m_pdate` contrario, el acceso producirá resultados poco fiables.

Para obtener más información acerca del tipo de datos TIMESTAMP_STRUCT, vea el tema Tipos de [datos C](/sql/odbc/reference/appendixes/c-data-types) en el Apéndice D de la referencia del *programador ODBC* en el Windows SDK.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant::m_pstring

Almacena un puntero a un objeto de tipo [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Observaciones

El `m_pstring` miembro de datos pertenece a una unión. Antes `m_pstring`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_pstring` DBVT_STRING, contiene un puntero válido; de lo `m_pstring` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant::m_pstringA

Almacena un puntero a un ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.

### <a name="remarks"></a>Observaciones

El `m_pstringA` miembro de datos pertenece a una unión. Antes `m_pstringA`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_pstringA` DBVT_ASTRING, contiene un puntero válido; de lo `m_pstringA` contrario, el acceso producirá resultados poco fiables.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant::m_pstringW

Almacena un puntero a un amplio [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.

### <a name="remarks"></a>Observaciones

El `m_pstringW` miembro de datos pertenece a una unión. Antes `m_pstringW`de acceder a , compruebe primero el valor de [CDBVariant::m_dwType](#m_dwtype). Si `m_dwType` se establece en `m_pstringW` DBVT_WSTRING, contiene un puntero válido; de lo `m_pstringW` contrario, el acceso producirá resultados poco fiables.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
