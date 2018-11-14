---
title: Clase COleVariant
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
ms.openlocfilehash: b37105cf1afdcf966176a2e2615f9c141022088d
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520523"
---
# <a name="colevariant-class"></a>Clase COleVariant

Encapsula el tipo de datos [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) .

## <a name="syntax"></a>Sintaxis

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleVariant::COleVariant](#colevariant)|Construye un objeto `COleVariant`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleVariant::Attach](#attach)|Adjunta una variante en una `COleVariant`.|
|[COleVariant::ChangeType](#changetype)|Cambia el tipo de variante de este `COleVariant` objeto.|
|[COleVariant::Clear](#clear)|Esto borra `COleVariant` objeto.|
|[COleVariant::Detach](#detach)|Desasocia una variante de un `COleVariant` y devuelve la variante.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Recupera una matriz de bytes de una matriz de variant existente.|
|[COleVariant::SetString](#setstring)|Establece la cadena a un tipo determinado, normalmente ANSI.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Convierte un `COleVariant` valor en un `LPCVARIANT`.|
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Convierte un `COleVariant` objeto en un `LPVARIANT`.|
|[COleVariant::operator =](#operator_eq)|Copia un `COleVariant` valor.|
|[COleVariant::operator ==](#operator_eq_eq)|Compara dos `COleVariant` valores.|
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Salidas un `COleVariant` valor `CArchive` o `CDumpContext` y los introduce un `COleVariant` objeto `CArchive`.|

## <a name="remarks"></a>Comentarios

Este tipo de datos se usa en la automatización OLE. En concreto, el [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams) estructura contiene un puntero a una matriz de estructuras VARIANT. Un `DISPPARAMS` estructura se usa para pasar parámetros al [IDispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Esta clase se deriva el `VARIANT` estructura. Esto significa que puede pasar un `COleVariant` en un parámetro que requiere un `VARIANT` y que los miembros de datos de la `VARIANT` estructura son miembros de datos accesibles de `COleVariant`.

Los dos relacionados con las clases MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) y [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsular los tipos de datos variant moneda ( `VT_CY`) y la fecha ( `VT_DATE`). El `COleVariant` clase se usa habitualmente en las clases DAO; Vea estas clases para un uso típico de esta clase, por ejemplo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Para obtener más información, consulte el [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [moneda](/windows/desktop/api/wtypes/ns-wtypes-tagcy), [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams), y [IDispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) entradas en el SDK de Windows.

Para obtener más información sobre la `COleVariant` clase y su uso en la automatización OLE, vea "Pasar parámetros de automatización OLE" en el artículo [automatización](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="attach"></a>  COleVariant::Attach

Llame a esta función para adjuntar el determinado [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) el objeto actual `COleVariant` objeto.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Existente `VARIANT` objeto que se adjuntará a la actual `COleVariant` objeto.

### <a name="remarks"></a>Comentarios

Esta función establece el valor de VARTYPE *varSrc* en VT_EMPTY.

Para obtener más información, consulte el [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) y [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) entradas en el SDK de Windows.

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
Existente `COleVariant` o `VARIANT` objeto que se copiará en el nuevo `COleVariant` objeto.

*pSrc*<br/>
Un puntero a un `VARIANT` objeto que se copiarán en el nuevo `COleVariant` objeto.

*lpszSrc*<br/>
Una cadena terminada en null que se copiará en el nuevo `COleVariant` objeto.

*vtSrc*<br/>
El `VARTYPE` para el nuevo `COleVariant` objeto.

*strSrc*<br/>
Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.

*nSrc*, *lSrc* un valor numérico que se copiará en el nuevo `COleVariant` objeto.

*vtSrc*<br/>
El `VARTYPE` para el nuevo `COleVariant` objeto.

*curSrc*<br/>
Un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.

*fltSrc*, *dblSrc*<br/>
Un valor numérico que se va a copiar en el nuevo objeto `COleVariant`.

*timeSrc*<br/>
Un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.

*arrSrc*<br/>
Un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.

*lbSrc*<br/>
Un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto que se copiará en el nuevo `COleVariant` objeto.

*PIDL*<br/>
Un puntero a un [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist) estructura que se copiará en el nuevo `COleVariant` objeto.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleVariant` objetos inicializados en el valor especificado. Una breve descripción de cada uno de estos constructores sigue.

- **() COleVariant** crea vacío `COleVariant` objeto, VT_EMPTY.

- **COleVariant (** *varSrc* **)** copia existente `VARIANT` o `COleVariant` objeto. El tipo variant se conserva.

- **COleVariant (** *pSrc* **)** copia existente `VARIANT` o `COleVariant` objeto. El tipo variant se conserva.

- **COleVariant (** *lpszSrc* **)** copia una cadena en el nuevo objeto, VT_BSTR (UNICODE).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** copia una cadena en el nuevo objeto. El parámetro *vtSrc* debe ser VT_BSTR (UNICODE) o VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** copia una cadena en el nuevo objeto, VT_BSTR (UNICODE).

- **COleVariant (** *nSrc* **)** copia un entero de 8 bits en el nuevo objeto, VT_UI1.

- **COleVariant (** *nSrc* **,** *vtSrc* **)** copia en el nuevo objeto de un entero de 16 bits (o valor booleano). El parámetro *vtSrc* debe ser VT_I2 o VT_BOOL.

- **COleVariant (** *lSrc* **,** *vtSrc* **)** copia en el nuevo objeto de un entero de 32 bits (o valor SCODE). El parámetro *vtSrc* debe ser VT_I4, VT_ERROR o VT_BOOL.

- **COleVariant (** *curSrc* **)** copias un `COleCurrency` valor en el nuevo objeto, VT_CY.

- **COleVariant (** *fltSrc* **)** copia un valor de punto flotante de 32 bits en el nuevo objeto, VT_R4.

- **COleVariant (** *dblSrc* **)** copia un valor de punto flotante de 64 bits en el nuevo objeto, VT_R8.

- **COleVariant (** *timeSrc* **)** copias un `COleDateTime` valor en el nuevo objeto, VT_DATE.

- **COleVariant (** *arrSrc* **)** copias un `CByteArray` objeto en el nuevo objeto, VT_EMPTY.

- **COleVariant (** *lbSrc* **)** copias un `CLongBinary` objeto en el nuevo objeto, VT_EMPTY.

Para obtener más información sobre SCODE, consulte [estructura de códigos de Error COM](/windows/desktop/com/structure-of-com-error-codes) en el SDK de Windows.

##  <a name="changetype"></a>  COleVariant::ChangeType

Convierte el tipo de valor de variante de este `COleVariant` objeto.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parámetros

*VarType*<br/>
El valor de VARTYPE para este `COleVariant` objeto.

*pSrc*<br/>
Un puntero a la [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) objeto va a convertir. Si este valor es NULL, esto `COleVariant` objeto se usa como origen para la conversión.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum), y [VariantChangeType](/windows/desktop/api/oleauto/nf-oleauto-variantchangetype) entradas en el SDK de Windows.

##  <a name="clear"></a>  COleVariant::Clear

Borra la `VARIANT`.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

Esto establece el valor de VARTYPE para este objeto en VT_EMPTY. El `COleVariant` destructor llama a esta función.

Para obtener más información, consulte el `VARIANT`, VARTYPE, y `VariantClear` entradas en el SDK de Windows.

##  <a name="detach"></a>  COleVariant::Detach

Desasocia subyacente [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) objeto desde este `COleVariant` objeto.

```
VARIANT Detach();
```

### <a name="remarks"></a>Comentarios

Esta función establece el valor de VARTYPE para este `COleVariant` objeto en VT_EMPTY.

> [!NOTE]
>  Después de llamar a `Detach`, es responsabilidad del llamador para llamar a `VariantClear` en resultante `VARIANT` estructura.

Para obtener más información, consulte el [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum), y [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) entradas en el SDK de Windows.

##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray

Recupera una matriz de bytes de una matriz de variant existente

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parámetros

*Bytes*<br/>
Una referencia a una existente [CByteArray](../../mfc/reference/cbytearray-class.md) objeto.

##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT

Este operador de conversión devuelve un `VARIANT` estructura cuyo valor se copia desde este `COleVariant` objeto.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Comentarios

##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT

Llamar a este operador de conversión para obtener acceso a subyacente `VARIANT` estructura para este `COleVariant` objeto.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Comentarios

> [!CAUTION]
> Cambia el valor en el `VARIANT` estructura accediendo el puntero devuelto por esta función cambiará el valor de esta `COleVariant` objeto.

##  <a name="operator_eq"></a>  COleVariant::operator =

Estos operadores de asignaciones sobrecargados copian el valor de origen en este `COleVariant` objeto.

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

- **operador = (** *varSrc* **)** copia una variante existente o `COleVariant` objeto en este objeto.

- **operador = (** *pSrc* **)** copia el objeto de variante accediendo a *pSrc* en este objeto.

- **operador = (** *lpszSrc* **)** copia una cadena terminada en null en este objeto y establece el valor de VARTYPE en VT_BSTR.

- **operador = (** *strSrc* **)** copias un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto en este objeto y establece el valor de VARTYPE en VT_BSTR.

- **operador = (** *nSrc* **)** copia un valor entero de 8 o 16 bits en este objeto. Si *nSrc* es un valor de 8 bits, el valor de VARTYPE esto está establecido en VT_UI1. Si *nSrc* es un valor de 16 bits y el valor de VARTYPE esto es VT_BOOL, mantenerse; de lo contrario, se establece en VT_I2.

- **operador = (** *lSrc* **)** copia un valor entero de 32 bits en este objeto. Si el valor de VARTYPE esto es VT_ERROR, se mantienen; en caso contrario, se establece en VT_I4.

- **operador = (** *curSrc* **)** copias un [COleCurrency](../../mfc/reference/colecurrency-class.md) objeto en este objeto y establece el valor de VARTYPE a VT_CY.

- **operador = (** *fltSrc* **)** copia un valor de punto flotante de 32 bits en este objeto y establece el valor de VARTYPE en VT_R4.

- **operador = (** *dblSrc* **)** copia un valor de punto flotante de 64 bits en este objeto y establece el valor de VARTYPE en VT_R8.

- **operador = (** *dateSrc* **)** copias un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto en este objeto y establece el valor de VARTYPE a VT_DATE.

- **operador = (** *arrSrc* **)** copias un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto `COleVariant` objeto.

- **operador = (** *lbSrc* **)** copias un [CLongBinary](../../mfc/reference/clongbinary-class.md) objeto `COleVariant` objeto.

Para obtener más información, consulte el [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) y [VARENUM](/windows/desktop/api/wtypes/ne-wtypes-varenum) entradas en el SDK de Windows.

##  <a name="operator_eq_eq"></a>  COleVariant::operator ==

Este operador compara dos valores variantes y devuelve cero si son iguales; en caso contrario, es 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;

Salidas un `COleVariant` valor `CArchive` o `CdumpContext` y los introduce un `COleVariant` objeto `CArchive`.

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

El `COleVariant` inserción (**\<\<**) admite el operador de volcado de diagnóstico y almacenar en un archivo. La extracción (**>>**) operador puede cargar desde un archivo.

##  <a name="setstring"></a>  COleVariant::SetString

Establece la cadena a un tipo determinado.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parámetros

*lpszSrc*<br/>
Una cadena terminada en null que se copiará en el nuevo `COleVariant` objeto.

*vtSrc*<br/>
El valor de VARTYPE para el nuevo `COleVariant` objeto.

### <a name="remarks"></a>Comentarios

El parámetro *vtSrc* debe ser VT_BSTR (UNICODE) o VT_BSTRT (ANSI). `SetString` Normalmente se usa para establecer las cadenas a ANSI, desde el valor predeterminado para el [COleVariant::COleVariant](#colevariant) constructor con una cadena o el parámetro de puntero de cadena y no VARTYPE es UNICODE.

Un conjunto de registros en una compilación que no son UNICODE espera que las cadenas ANSI. Para DAO por lo tanto, las funciones que usan `COleVariant` objetos, si no va a crear un conjunto de registros UNICODE, debe usar el **COleVariant::COleVariant (** *lpszSrc* **,** *vtSrc* **)** formulario del constructor con *vtSrc* establezca VT_BSTRT (ANSI) o use `SetString` con *vtSrc* establecido en VT _BSTRT hacer cadenas ANSI. Por ejemplo, el `CDaoRecordset` funciones [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) y [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) usar `COleVariant` objetos como parámetros. Estos objetos deben ser ANSI si el conjunto de registros DAO no es UNICODE.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
