---
title: COleVariant (clase)
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 49cd4a8d3db436d5e3c4d29efbb4d80b4741a270
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739789"
---
# <a name="colevariant-class"></a>COleVariant (clase)

Encapsula el tipo de datos [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) .

## <a name="syntax"></a>Sintaxis

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleVariant::COleVariant](#colevariant)|Construye un objeto `COleVariant`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleVariant::Attach](#attach)|Adjunta una variante a un `COleVariant`.|
|[COleVariant::ChangeType](#changetype)|Cambia el tipo de variante de `COleVariant` este objeto.|
|[COleVariant::Clear](#clear)|Borra este `COleVariant` objeto.|
|[COleVariant::Detach](#detach)|Desasocia una variante de `COleVariant` y devuelve la variante.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Recupera una matriz de bytes de una matriz de variantes existente.|
|[COleVariant::SetString](#setstring)|Establece la cadena en un tipo determinado, normalmente ANSI.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleVariant:: Operator LPCVARIANT](#operator_lpcvariant)|Convierte un `COleVariant` valor `LPCVARIANT`en.|
|[COleVariant:: Operator LPVARIANT](#operator_lpvariant)|Convierte un `COleVariant` objeto `LPVARIANT`en.|
|[COleVariant:: Operator =](#operator_eq)|Copia un `COleVariant` valor.|
|[COleVariant:: Operator = =](#operator_eq_eq)|Compara dos `COleVariant` valores.|
|[COleVariant:: ( &lt;operador &lt;),&gt;&gt;](#operator_lt_lt__gt_gt)|Envía un `COleVariant` valor a `CArchive` o `CDumpContext` y escribe un `COleVariant` objeto de `CArchive`.|

## <a name="remarks"></a>Comentarios

Este tipo de datos se utiliza en la automatización OLE. En concreto, la estructura [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) contiene un puntero a una matriz de estructuras variantes. Una `DISPPARAMS` estructura se utiliza para pasar parámetros a [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Esta clase se deriva de la `VARIANT` estructura. Esto significa que puede pasar un `COleVariant` en un parámetro que llama a para `VARIANT` un y que los miembros de datos `VARIANT` de la estructura son miembros de `COleVariant`datos accesibles de.

Las dos clases MFC relacionadas [COleCurrency](../../mfc/reference/colecurrency-class.md) y [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsulan los tipos de datos Variant Currency `VT_CY`() y Date `VT_DATE`(). La `COleVariant` clase se utiliza exhaustivamente en las clases DAO; vea estas clases para el uso típico de esta clase, por ejemplo, [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Para obtener más información, vea las entradas [Variant](/windows/win32/api/oaidl/ns-oaidl-variant), [Currency](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)y [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) en el Windows SDK.

Para obtener más información sobre `COleVariant` la clase y su uso en la automatización OLE, vea "pasar parámetros en la automatización OLE" en el artículo [automatización](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="attach"></a>  COleVariant::Attach

Llame a esta función para asociar el objeto [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) dado al `COleVariant` objeto actual.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto existente `VARIANT` que se va a adjuntar `COleVariant` al objeto actual.

### <a name="remarks"></a>Comentarios

Esta función establece el VARTYPE de *varSrc* en VT_EMPTY.

Para obtener más información, vea las entradas [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) y [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) en el Windows SDK.

##  <a name="colevariant"></a>  COleVariant::COleVariant

Construye un objeto `COleVariant`.

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto o `COleVariant` `VARIANT` existente que se va a copiar en el `COleVariant` nuevo objeto.

*pSrc*<br/>
Un puntero a un `VARIANT` objeto que se copiará en el nuevo `COleVariant` objeto.

*lpszSrc*<br/>
Una cadena terminada en null que se va a copiar `COleVariant` en el nuevo objeto.

*vtSrc*<br/>
Del `VARTYPE` nuevo`COleVariant` objeto.

*strSrc*<br/>
Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que se va a copiar en el `COleVariant` nuevo objeto.

*nSrc*, *lSrc* un valor numérico que se va a copiar en `COleVariant` el nuevo objeto.

*vtSrc*<br/>
Del `VARTYPE` nuevo`COleVariant` objeto.

*curSrc*<br/>
Objeto [COleCurrency](../../mfc/reference/colecurrency-class.md) que se va a copiar en el `COleVariant` nuevo objeto.

*fltSrc*, *dblSrc*<br/>
Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.

*timeSrc*<br/>
Objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) que se va a copiar en el `COleVariant` nuevo objeto.

*arrSrc*<br/>
Objeto [CByteArray](../../mfc/reference/cbytearray-class.md) que se va a copiar en el `COleVariant` nuevo objeto.

*lbSrc*<br/>
Objeto [CLongBinary](../../mfc/reference/clongbinary-class.md) que se va a copiar en el `COleVariant` nuevo objeto.

*pidl*<br/>
Puntero a una estructura [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) que se va a copiar en el `COleVariant` nuevo objeto.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleVariant` objetos inicializados en el valor especificado. A continuación se muestra una breve descripción de cada uno de estos constructores.

- **COleVariant ()** Crea un objeto `COleVariant` vacío, VT_EMPTY.

- **COleVariant (** *varSrc* **)** Copia un objeto `VARIANT` o `COleVariant` existente. El tipo variant se conserva.

- **COleVariant (** *pSrc* **)** Copia un objeto `VARIANT` o `COleVariant` existente. El tipo variant se conserva.

- **COleVariant (** *lpszSrc* **)** Copia una cadena en el nuevo objeto, VT_BSTR (Unicode).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** Copia una cadena en el nuevo objeto. El parámetro *vtSrc* debe ser VT_BSTR (Unicode) o VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** Copia una cadena en el nuevo objeto, VT_BSTR (Unicode).

- **COleVariant (** *nSrc* **)** Copia un entero de 8 bits en el nuevo objeto, VT_UI1.

- **COleVariant (** *nSrc* **,** *vtSrc* **)** Copia un entero de 16 bits (o un valor booleano) en el nuevo objeto. El parámetro *vtSrc* debe ser VT_I2 o VT_BOOL.

- **COleVariant (** *lSrc* **,** *vtSrc* **)** Copia un entero de 32 bits (o el valor SCODE) en el nuevo objeto. El parámetro *vtSrc* debe ser VT_I4, VT_ERROR o VT_BOOL.

- **COleVariant (** *curSrc* **)** Copia un `COleCurrency` valor en el nuevo objeto VT_CY.

- **COleVariant (** *fltSrc* **)** Copia un valor de punto flotante de 32 bits en el nuevo objeto, VT_R4.

- **COleVariant (** *dblSrc* **)** Copia un valor de punto flotante de 64 bits en el nuevo objeto, VT_R8.

- **COleVariant (** *timeSrc* **)** Copia un `COleDateTime` valor en el nuevo objeto, VT_DATE.

- **COleVariant (** *arrSrc* **)** Copia un `CByteArray` objeto en el nuevo objeto, VT_EMPTY.

- **COleVariant (** *lbSrc* **)** Copia un `CLongBinary` objeto en el nuevo objeto, VT_EMPTY.

Para obtener más información sobre SCODE, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

##  <a name="changetype"></a>  COleVariant::ChangeType

Convierte el tipo de valor Variant de este `COleVariant` objeto.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parámetros

*vartype*<br/>
VARTYPE para este `COleVariant` objeto.

*pSrc*<br/>
Puntero al objeto [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) que se va a convertir. Si este valor es null, este `COleVariant` objeto se utiliza como el origen de la conversión.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea las entradas [Variant](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)y [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) en el Windows SDK.

##  <a name="clear"></a>  COleVariant::Clear

Borra el `VARIANT`.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

Esto establece el VARTYPE de este objeto en VT_EMPTY. El `COleVariant` destructor llama a esta función.

Para obtener más información, vea `VARIANT`las entradas, VARTYPE `VariantClear` y en el Windows SDK.

##  <a name="detach"></a>  COleVariant::Detach

Desasocia el objeto [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) subyacente de este `COleVariant` objeto.

```
VARIANT Detach();
```

### <a name="remarks"></a>Comentarios

Esta función establece el VARTYPE para este `COleVariant` objeto en VT_EMPTY.

> [!NOTE]
>  Después de `Detach`llamar a, es responsabilidad del llamador llamar `VariantClear` a en la estructura `VARIANT` resultante.

Para obtener más información, vea las entradas [Variant](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)y [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) en el Windows SDK.

##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray

Recupera una matriz de bytes de una matriz de variantes existente.

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parámetros

*bytes*<br/>
Referencia a un objeto [CByteArray](../../mfc/reference/cbytearray-class.md) existente.

##  <a name="operator_lpcvariant"></a>COleVariant:: Operator LPCVARIANT

Este operador de conversión devuelve `VARIANT` una estructura cuyo valor se copia de `COleVariant` este objeto.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Comentarios

##  <a name="operator_lpvariant"></a>COleVariant:: Operator LPVARIANT

Llame a este operador de conversión para tener `VARIANT` acceso a la `COleVariant` estructura subyacente de este objeto.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Comentarios

> [!CAUTION]
> Al cambiar el valor de `VARIANT` la estructura a la que accede el puntero devuelto por esta función, cambiará `COleVariant` el valor de este objeto.

##  <a name="operator_eq"></a>COleVariant:: Operator =

Estos operadores de asignación sobrecargados copian el valor de `COleVariant` origen en este objeto.

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>Comentarios

A continuación se muestra una breve descripción de cada operador:

- **Operator = (** *varSrc* **)** Copia una variante u `COleVariant` objeto existente en este objeto.

- **Operator = (** *pSrc* **)** Copia el objeto variante al que tiene acceso *pSrc* en este objeto.

- **Operator = (** *lpszSrc* **)** Copia una cadena terminada en null en este objeto y establece VARTYPE en VT_BSTR.

- **Operator = (** *strSrc* **)** Copia un objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) en este objeto y establece VARTYPE en VT_BSTR.

- **Operator = (** *nSrc* **)** Copia un valor entero de 8 o 16 bits en este objeto. Si *nSrc* es un valor de 8 bits, el VARTYPE de se establece en VT_UI1. Si *nSrc* es un valor de 16 bits y el VARTYPE de este es VT_BOOL, se mantiene; de lo contrario, se establece en VT_I2.

- **Operator = (** *lSrc* **)** Copia un valor entero de 32 bits en este objeto. Si el VARTYPE de este es VT_ERROR, se mantiene; de lo contrario, se establece en VT_I4.

- **Operator = (** *curSrc* **)** Copia un objeto [COleCurrency](../../mfc/reference/colecurrency-class.md) en este objeto y establece VARTYPE en VT_CY.

- **Operator = (** *fltSrc* **)** Copia un valor de punto flotante de 32 bits en este objeto y establece VARTYPE en VT_R4.

- **Operator = (** *dblSrc* **)** Copia un valor de punto flotante de 64 bits en este objeto y establece VARTYPE en VT_R8.

- **Operator = (** *dateSrc* **)** Copia un objeto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) en este objeto y establece VARTYPE en VT_DATE.

- **Operator = (** *arrSrc* **)** Copia un objeto [CByteArray](../../mfc/reference/cbytearray-class.md) en este `COleVariant` objeto.

- **Operator = (** *lbSrc* **)** Copia un objeto [CLongBinary](../../mfc/reference/clongbinary-class.md) en este `COleVariant` objeto.

Para obtener más información, vea las entradas [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) y [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) en el Windows SDK.

##  <a name="operator_eq_eq"></a>COleVariant:: Operator = =

Este operador compara dos valores de variante y devuelve un valor distinto de cero si son iguales; de lo contrario, es 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>COleVariant:: ( &lt;operador &lt;),&gt;&gt;

Envía un `COleVariant` valor a `CArchive` o `CdumpContext` y escribe un `COleVariant` objeto de `CArchive`.

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>Comentarios

El `COleVariant` operador de **\<inserción(\<** ) admite el volcado y el almacenamiento de diagnósticos en un archivo. El operador de **>>** extracción () permite cargar desde un archivo.

##  <a name="setstring"></a>  COleVariant::SetString

Establece la cadena en un tipo determinado.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parámetros

*lpszSrc*<br/>
Una cadena terminada en null que se va a copiar `COleVariant` en el nuevo objeto.

*VtSrc*<br/>
VARTYPE del nuevo `COleVariant` objeto.

### <a name="remarks"></a>Comentarios

El parámetro *vtSrc* debe ser VT_BSTR (Unicode) o VT_BSTRT (ANSI). `SetString`se utiliza normalmente para establecer cadenas en ANSI, dado que el valor predeterminado para el constructor [COleVariant:: COleVariant](#colevariant) con un parámetro de cadena o de puntero de cadena y ningún VARTYPE es Unicode.

Un conjunto de registros DAO en una compilación no Unicode espera que las cadenas sean ANSI. Por lo tanto, para las funciones `COleVariant` DAO que usan objetos, si no está creando un conjunto de registros Unicode, debe usar la forma **COleVariant:: COleVariant (** *lpszSrc* **,** *vtSrc* **)** del constructor con *vtSrc* establecido en VT. _BSTRT (ANSI) o use `SetString` con *vtSrc* establecido en VT_BSTRT para crear cadenas ANSI. Por ejemplo, las `CDaoRecordset` funciones [CDaoRecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek) y [CDaoRecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) usan `COleVariant` objetos como parámetros. Estos objetos deben ser ANSI si el conjunto de registros DAO no es Unicode.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
