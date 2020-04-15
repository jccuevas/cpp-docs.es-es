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
ms.openlocfilehash: f907ed7c058f87cf03530411bc8fa4a3c108a4f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374825"
---
# <a name="colevariant-class"></a>COleVariant (clase)

Encapsula el tipo de datos [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) .

## <a name="syntax"></a>Sintaxis

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleVariant::COleVariant](#colevariant)|Construye un objeto `COleVariant`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleVariant::Attach](#attach)|Asocia un VARIANT `COleVariant`a un archivo .|
|[COleVariant::ChangeType](#changetype)|Cambia el tipo `COleVariant` de variante de este objeto.|
|[COleVariant::Clear](#clear)|Borra este objeto `COleVariant`.|
|[COleVariant::Detach](#detach)|Separa un VARIANT `COleVariant` de a y devuelve el VARIANT.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Recupera una matriz de bytes de una matriz de variantes existente.|
|[COleVariant::SetString](#setstring)|Establece la cadena en un tipo determinado, normalmente ANSI.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleVariant::operador LPCVARIANT](#operator_lpcvariant)|Convierte un `COleVariant` valor `LPCVARIANT`en un archivo .|
|[COleVariant::operador LPVARIANT](#operator_lpvariant)|Convierte un `COleVariant` objeto `LPVARIANT`en un archivo .|
|[COleVariant::operador ?](#operator_eq)|Copia `COleVariant` un valor.|
|[COleVariant::operador ?](#operator_eq_eq)|Compara dos `COleVariant` valores.|
|[COleVariant::operador &lt; &lt;,&gt;&gt;](#operator_lt_lt__gt_gt)|Emite un `COleVariant` valor `CArchive` `CDumpContext` a o `COleVariant` e `CArchive`introduce un objeto desde .|

## <a name="remarks"></a>Observaciones

Este tipo de datos se utiliza en la automatización OLE. En concreto, la estructura [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) contiene un puntero a una matriz de estructuras VARIANT. Se `DISPPARAMS` utiliza una estructura para pasar parámetros a [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Esta clase se deriva `VARIANT` de la estructura. Esto significa que `COleVariant` puede pasar un parámetro `VARIANT` que llama a `VARIANT` y que los `COleVariant`miembros de datos de la estructura son miembros de datos accesibles de .

Las dos clases MFC relacionadas [COleCurrency](../../mfc/reference/colecurrency-class.md) y [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsulan los tipos de datos de variante CURRENCY ( `VT_CY`) y DATE ( `VT_DATE`). La `COleVariant` clase se utiliza ampliamente en las clases DAO; ver estas clases para el uso típico de esta clase, por ejemplo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Para obtener más información, vea las entradas [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)e [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) en el Windows SDK.

Para obtener más `COleVariant` información sobre la clase y su uso en la automatización OLE, vea "Pasar parámetros en la automatización OLE" en el artículo [Automatización](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant::Attach

Llame a esta función para asociar `COleVariant` el objeto [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) especificado al objeto actual.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto `VARIANT` existente que se va `COleVariant` a adjuntar al objeto actual.

### <a name="remarks"></a>Observaciones

Esta función establece el VARTYPE de *varSrc* en VT_EMPTY.

Para obtener más información, consulte las entradas [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) y [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) en el Windows SDK.

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant::COleVariant

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
Un `COleVariant` objeto `VARIANT` u objeto existente que `COleVariant` se va a copiar en el nuevo objeto.

*pSrc*<br/>
Puntero a `VARIANT` un objeto que se copiará en el nuevo `COleVariant` objeto.

*lpszSrc*<br/>
Cadena terminada en null que se va `COleVariant` a copiar en el nuevo objeto.

*vtSrc*<br/>
El `VARTYPE` para `COleVariant` el nuevo objeto.

*strSrc*<br/>
Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se `COleVariant` va a copiar en el nuevo objeto.

*nSrc*, *lSrc* Un valor numérico que `COleVariant` se va a copiar en el nuevo objeto.

*vtSrc*<br/>
El `VARTYPE` para `COleVariant` el nuevo objeto.

*curSrc*<br/>
Un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto que se `COleVariant` va a copiar en el nuevo objeto.

*fltSrc*, *dblSrc*<br/>
Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.

*timeSrc*<br/>
Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que se `COleVariant` va a copiar en el nuevo objeto.

*arrSrc*<br/>
Un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto que se `COleVariant` va a copiar en el nuevo objeto.

*lbSrc*<br/>
Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto que se `COleVariant` va a copiar en el nuevo objeto.

*pidl*<br/>
Puntero a una estructura [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) que se `COleVariant` va a copiar en el nuevo objeto.

### <a name="remarks"></a>Observaciones

Todos estos constructores `COleVariant` crean nuevos objetos inicializados en el valor especificado. A continuación se ofrece una breve descripción de cada uno de estos constructores.

- **COleVariant( )** Crea un `COleVariant` objeto vacío, VT_EMPTY.

- **COleVariant(** *varSrc* **)** Copia un `VARIANT` `COleVariant` objeto u existente. El tipo variant se conserva.

- **COleVariant(** *pSrc* **)** Copia un `VARIANT` `COleVariant` objeto u existente. El tipo variant se conserva.

- **COleVariant(** *lpszSrc* **)** Copia una cadena en el nuevo objeto, VT_BSTR (UNICODE).

- **COleVariant(** *lpszSrc* **,** *vtSrc* **)** Copia una cadena en el nuevo objeto. El parámetro *vtSrc* debe estar VT_BSTR (UNICODE) o VT_BSTRT (ANSI).

- **COleVariant(** *strSrc* **)** Copia una cadena en el nuevo objeto, VT_BSTR (UNICODE).

- **COleVariant(** *nSrc* **)** Copia un entero de 8 bits en el nuevo objeto, VT_UI1.

- **COleVariant(** *nSrc* **,** *vtSrc* **)** Copia un entero de 16 bits (o valor booleano) en el nuevo objeto. El parámetro *vtSrc* debe estar VT_I2 o VT_BOOL.

- **COleVariant(** *lSrc* **,** *vtSrc* **)** Copia un entero de 32 bits (o valor SCODE) en el nuevo objeto. El parámetro *vtSrc* debe ser VT_I4, VT_ERROR o VT_BOOL.

- **COleVariant(** *curSrc* **)** Copia `COleCurrency` un valor en el nuevo objeto, VT_CY.

- **COleVariant(** *fltSrc* **)** Copia un valor de punto flotante de 32 bits en el nuevo objeto, VT_R4.

- **COleVariant(** *dblSrc* **)** Copia un valor de punto flotante de 64 bits en el nuevo objeto, VT_R8.

- **COleVariant(** *timeSrc* **)** Copia `COleDateTime` un valor en el nuevo objeto, VT_DATE.

- **COleVariant(** *arrSrc* **)** Copia `CByteArray` un objeto en el nuevo objeto, VT_EMPTY.

- **COleVariant(** *lbSrc* **)** Copia `CLongBinary` un objeto en el nuevo objeto, VT_EMPTY.

Para obtener más información sobre SCODE, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant::ChangeType

Convierte el tipo de valor `COleVariant` de variante en este objeto.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parámetros

*Vartype*<br/>
El VARTYPE `COleVariant` para este objeto.

*pSrc*<br/>
Puntero al objeto [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) que se va a convertir. Si este valor es `COleVariant` NULL, este objeto se utiliza como origen para la conversión.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea las entradas [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)y [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) en el Windows SDK.

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant::Clear

Borra la colección `VARIANT`.

```
void Clear();
```

### <a name="remarks"></a>Observaciones

Esto establece el VARTYPE para este objeto en VT_EMPTY. El `COleVariant` destructor llama a esta función.

Para obtener más `VARIANT`información, vea `VariantClear` el , VARTYPE y entradas en el Windows SDK.

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::Detach

Separa el objeto [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) subyacente `COleVariant` de este objeto.

```
VARIANT Detach();
```

### <a name="remarks"></a>Observaciones

Esta función establece el `COleVariant` VARTYPE para este objeto en VT_EMPTY.

> [!NOTE]
> Después `Detach`de llamar , es responsabilidad `VariantClear` del `VARIANT` autor de la llamada llamar a la estructura resultante.

Para obtener más información, vea las entradas [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)y [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) en el Windows SDK.

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray

Recupera una matriz de bytes de una matriz de variantes existente

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parámetros

*Bytes*<br/>
Una referencia a un objeto [CByteArray](../../mfc/reference/cbytearray-class.md) existente.

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant::operador LPCVARIANT

Este operador de `VARIANT` conversión devuelve una `COleVariant` estructura cuyo valor se copia de este objeto.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Observaciones

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant::operador LPVARIANT

Llame a este operador de `VARIANT` conversión `COleVariant` para tener acceso a la estructura subyacente de este objeto.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Observaciones

> [!CAUTION]
> Cambiar el valor `VARIANT` de la estructura a la que tiene `COleVariant` acceso el puntero devuelto por esta función cambiará el valor de este objeto.

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant::operador ?

Estos operadores de asignación sobrecargados copian el valor de origen en este `COleVariant` objeto.

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

### <a name="remarks"></a>Observaciones

A continuación se ofrece una breve descripción de cada operador:

- **operador (** *varSrc* **)** Copia un VARIANT `COleVariant` u objeto existente en este objeto.

- **Operador** *(pSrc* **)** Copia el objeto VARIANT al que tiene acceso *pSrc* en este objeto.

- **operador (** *lpszSrc* **)** Copia una cadena terminada en null en este objeto y establece el VARTYPE en VT_BSTR.

- **Operador (** *strSrc* **)** Copia un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto en este objeto y establece el VARTYPE en VT_BSTR.

- **operador** *(nSrc* **)** Copia un valor entero de 8 o 16 bits en este objeto. Si *nSrc* es un valor de 8 bits, el VARTYPE de esto se establece en VT_UI1. Si *nSrc* es un valor de 16 bits y el VARTYPE de esto es VT_BOOL, se mantiene; de lo contrario, se establece en VT_I2.

- **Operador** *(lSrc* **)** Copia un valor entero de 32 bits en este objeto. Si el VARTYPE de esto es VT_ERROR, se mantiene; de lo contrario, se establece en VT_I4.

- **operador (** *curSrc* **)** Copia un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto en este objeto y establece el VARTYPE en VT_CY.

- **operador** *(fltSrc* **)** Copia un valor de punto flotante de 32 bits en este objeto y establece el VARTYPE en VT_R4.

- **Operador** *(dblSrc* **)** Copia un valor de punto flotante de 64 bits en este objeto y establece varTYPE en VT_R8.

- **operador (** *dateSrc* **)** Copia un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto en este objeto y establece el VARTYPE en VT_DATE.

- **Operador** *(arrSrc* **)** Copia un [CByteArray](../../mfc/reference/cbytearray-class.md) `COleVariant` objeto en este objeto.

- **operador (** *lbSrc* **)** Copia un [CLongBinary](../../mfc/reference/clongbinary-class.md) `COleVariant` objeto en este objeto.

Para obtener más información, consulte las entradas [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) y [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) en el Windows SDK.

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant::operador ?

Este operador compara dos valores de variante y devuelve distinto de cero si son iguales; de lo contrario 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant::operador &lt; &lt;,&gt;&gt;

Emite un `COleVariant` valor `CArchive` `CdumpContext` a o `COleVariant` e `CArchive`introduce un objeto desde .

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

### <a name="remarks"></a>Observaciones

El `COleVariant` operador**\<** de inserción ( ) admite el volcado de diagnóstico y el almacenamiento en un archivo. El operador**>>** de extracción ( ) admite la carga desde un archivo.

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant::SetString

Establece la cadena en un tipo determinado.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parámetros

*lpszSrc*<br/>
Cadena terminada en null que se va `COleVariant` a copiar en el nuevo objeto.

*VtSrc*<br/>
El VARTYPE para `COleVariant` el nuevo objeto.

### <a name="remarks"></a>Observaciones

El parámetro *vtSrc* debe estar VT_BSTR (UNICODE) o VT_BSTRT (ANSI). `SetString`normalmente se utiliza para establecer cadenas en ANSI, ya que el valor predeterminado para el [COleVariant::COleVariant](#colevariant) constructor con un parámetro de puntero de cadena o cadena y ningún VARTYPE es UNICODE.

Un conjunto de registros DAO en una compilación que no es UNICODE espera que las cadenas sean ANSI. Por lo tanto, `COleVariant` para las funciones DAO que utilizan objetos, si no está creando un conjunto de registros UNICODE, debe usar la forma **COleVariant::COleVariant(** *lpszSrc* **,** *vtSrc* **)** de constructor con *vtSrc* establecido en VT_BSTRT (ANSI) o usar `SetString` con *vtSrc* establecido para VT_BSTRT para crear cadenas ANSI. Por ejemplo, `CDaoRecordset` las funciones [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) y [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) utilizan `COleVariant` objetos como parámetros. Estos objetos deben ser ANSI si el conjunto de registros DAO no es UNICODE.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
