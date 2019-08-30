---
title: Clase COleSafeArray
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: a0ce0fc03923806c9e044a7edae3178fd3429b76
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177400"
---
# <a name="colesafearray-class"></a>Clase COleSafeArray

Una clase para trabajar con matrices de tipo y dimensión arbitrarios.

## <a name="syntax"></a>Sintaxis

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Construye un objeto `COleSafeArray`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Recupera un puntero a los datos de la matriz.|
|[COleSafeArray::AllocData](#allocdata)|Asigna memoria para la matriz.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Asigna memoria para el descriptor seguro de la matriz.|
|[COleSafeArray::Attach](#attach)|Proporciona el control de la `VARIANT` matriz existente `COleSafeArray` al objeto.|
|[COleSafeArray::Clear](#clear)|Libera todos los datos del subyacente `VARIANT`.|
|[COleSafeArray::Copy](#copy)|Crea una copia de una matriz existente.|
|[COleSafeArray::Create](#create)|Crea una matriz segura.|
|[COleSafeArray::CreateOneDim](#createonedim)|Crea un objeto unidimensional `COleSafeArray` .|
|[COleSafeArray::Destroy](#destroy)|Destruye una matriz existente.|
|[COleSafeArray::DestroyData](#destroydata)|Destruye los datos de una matriz segura.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Destruye un descriptor de una matriz segura.|
|[COleSafeArray::Detach](#detach)|Desasocia la matriz de variantes del `COleSafeArray` objeto (para que no se liberen los datos).|
|[COleSafeArray::GetByteArray](#getbytearray)|Copia el contenido de la matriz segura en una [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Devuelve el número de dimensiones de la matriz.|
|[COleSafeArray::GetElement](#getelement)|Recupera un único elemento de la matriz segura.|
|[COleSafeArray::GetElemSize](#getelemsize)|Devuelve el tamaño, en bytes, de un elemento de una matriz segura.|
|[COleSafeArray::GetLBound](#getlbound)|Devuelve el límite inferior para cualquier dimensión de una matriz segura.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Devuelve el número de elementos de un objeto unidimensional `COleSafeArray` .|
|[COleSafeArray::GetUBound](#getubound)|Devuelve el límite superior de cualquier dimensión de una matriz segura.|
|[COleSafeArray::Lock](#lock)|Incrementa el recuento de bloqueos de una matriz y coloca un puntero a los datos de la matriz en el descriptor de la matriz.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Devuelve un puntero al elemento indizado.|
|[COleSafeArray::PutElement](#putelement)|Asigna un único elemento en la matriz.|
|[COleSafeArray::Redim](#redim)|Cambia el límite menos significativo (derecho) de una matriz segura.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Cambia el número de elementos de un objeto unidimensional `COleSafeArray` .|
|[COleSafeArray::UnaccessData](#unaccessdata)|Disminuye el recuento de bloqueos de una matriz e invalida el puntero recuperado `AccessData`por.|
|[COleSafeArray::Unlock](#unlock)|Disminuye el recuento de bloqueos de una matriz para que se pueda liberar o cambiar de tamaño.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleSafeArray:: Operator LPCVARIANT](#operator_lpcvariant)|Obtiene acceso a la `VARIANT` estructura subyacente `COleSafeArray` del objeto.|
|[COleSafeArray:: Operator LPVARIANT](#operator_lpvariant)|Obtiene acceso a la `VARIANT` estructura subyacente `COleSafeArray` del objeto.|
|[COleSafeArray:: Operator =](#operator_eq)|Copia los valores en `COleSafeArray` un objeto`SAFEARRAY`( `VARIANT`, `COleVariant`, o `COleSafeArray` matriz).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Compara`SAFEARRAY`dos matrices variantes ( `VARIANT` `COleVariant`matrices,, o `COleSafeArray` ).|
|[COleSafeArray:: Operator&lt;&lt;](#operator_lt_lt)|Envía el contenido de un `COleSafeArray` objeto al contexto de volcado de memoria.|

## <a name="remarks"></a>Comentarios

`COleSafeArray`deriva de la estructura OLE `VARIANT` . Las funciones `SAFEARRAY` miembro de OLE están disponibles `COleSafeArray`a través de, así como un conjunto de funciones miembro diseñadas específicamente para matrices unidimensionales de bytes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

Recupera un puntero a los datos de la matriz.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parámetros

*ppvData*<br/>
Un puntero a un puntero a los datos de la matriz.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

Asigna memoria para una matriz segura.

```
void AllocData();
```

### <a name="remarks"></a>Comentarios

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

Asigna memoria para el descriptor de una matriz segura.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parámetros

*dwDims*<br/>
Número de dimensiones de la matriz segura.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="attach"></a>  COleSafeArray::Attach

Proporciona el `VARIANT` `COleSafeArray` control de los datos de una matriz existente al objeto.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto `VARIANT`. El parámetro *varSrc* debe tener el [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)de VARTYPE.

### <a name="remarks"></a>Comentarios

El tipo `VARIANT`de origen se establece en VT_EMPTY. Esta función borra los datos de la matriz actual, si los hay.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray:: AccessData](#accessdata).

##  <a name="clear"></a>  COleSafeArray::Clear

Borra la matriz segura.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

La función borra una matriz segura estableciendo el `VARTYPE` del objeto en VT_EMPTY. Se libera el contenido actual y se libera la matriz.

##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray

Construye un objeto `COleSafeArray`.

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>Parámetros

*saSrc*<br/>
Objeto existente `COleSafeArray` o `SAFEARRAY` que se va a copiar en el `COleSafeArray` nuevo objeto.

*vtSrc*<br/>
VARTYPE del nuevo `COleSafeArray` objeto.

*psaSrc*<br/>
Un puntero a un `SAFEARRAY` que se va a copiar en `COleSafeArray` el nuevo objeto.

*varSrc*<br/>
Objeto o `VARIANT` `COleVariant` existente que se va a copiar en el `COleSafeArray` nuevo objeto.

*pSrc*<br/>
Un puntero a un `VARIANT` objeto que se va a copiar en `COleSafeArray` el nuevo objeto.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleSafeArray` objetos. Si no hay ningún parámetro, se crea `COleSafeArray` un objeto vacío (VT_EMPTY). Si se copia de otra matriz cuyo VarType se conoce implícitamente (a `COleSafeArray`, `COleVariant`o `VARIANT`), el VARTYPE de la matriz de origen se conserva y no es necesario especificarlo. `COleSafeArray` Si se copia desde otra matriz cuyo VarType no es conocido (`SAFEARRAY`), el VarType debe especificarse en el parámetro *vtSrc* . `COleSafeArray`

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="copy"></a>  COleSafeArray::Copy

Crea una copia de una matriz segura existente.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parámetros

*ppsa*<br/>
Puntero a una ubicación en la que se va a devolver el nuevo descriptor de la matriz.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="create"></a>  COleSafeArray::Create

Asigna e inicializa los datos de la matriz.

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>Parámetros

*vtSrc*<br/>
El tipo base de la matriz (es decir, el VARTYPE de cada elemento de la matriz). VARTYPE está restringido a un subconjunto de los tipos Variant. No se puede establecer VT_ARRAY ni la marca VT_BYREF. VT_EMPTY y VT_NULL no son tipos base válidos para la matriz. Todos los demás tipos son válidos.

*dwDims*<br/>
Número de dimensiones de la matriz. Se puede cambiar después de crear la matriz con [ReDim](#redim).

*rgElements*<br/>
Puntero a una matriz del número de elementos de cada dimensión de la matriz.

*rgsabounds*<br/>
Puntero a un vector de límites (uno para cada dimensión) que se va a asignar a la matriz.

### <a name="remarks"></a>Comentarios

Esta función borrará los datos de la matriz actual, si es necesario. En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

Crea un nuevo objeto unidimensional `COleSafeArray` .

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parámetros

*vtSrc*<br/>
El tipo base de la matriz (es decir, el VARTYPE de cada elemento de la matriz).

*dwElements*<br/>
Número de elementos de la matriz. Esto puede cambiarse después de crear la matriz con [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Puntero a los datos que se van a copiar en la matriz.

*nLBound*<br/>
Límite inferior de la matriz.

### <a name="remarks"></a>Comentarios

La función asigna e inicializa los datos de la matriz, copiando los datos especificados si el puntero *pvSrcData* no es NULL.

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

Destruye un descriptor de matriz existente y todos los datos de la matriz.

```
void Destroy();
```

### <a name="remarks"></a>Comentarios

Si los objetos se almacenan en la matriz, se liberan todos los objetos. En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

Destruye todos los datos de una matriz segura.

```
void DestroyData();
```

### <a name="remarks"></a>Comentarios

Si los objetos se almacenan en la matriz, se liberan todos los objetos. En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

Destruye un descriptor de una matriz segura.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Comentarios

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="detach"></a>  COleSafeArray::Detach

Desasocia los `VARIANT` datos `COleSafeArray` del objeto.

```
VARIANT Detach();
```

### <a name="return-value"></a>Valor devuelto

`VARIANT` Valor`COleSafeArray` subyacente del objeto.

### <a name="remarks"></a>Comentarios

La función desasocia los datos de una matriz segura estableciendo el VARTYPE del objeto en VT_EMPTY. Es responsabilidad del llamador liberar la matriz mediante una llamada a la función de Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

En el error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::P utelement](#putelement).

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

Copia el contenido de la matriz segura en un `CByteArray`.

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parámetros

*bytes*<br/>
Referencia a un objeto [CByteArray](../../mfc/reference/cbytearray-class.md) .

##  <a name="getdim"></a>  COleSafeArray::GetDim

Devuelve el número de dimensiones `COleSafeArray` del objeto.

```
DWORD GetDim();
```

### <a name="return-value"></a>Valor devuelto

El número de dimensiones de la matriz segura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  COleSafeArray::GetElement

Recupera un único elemento de la matriz segura.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Puntero a una matriz de índices para cada dimensión de la matriz.

*pvData*<br/>
Puntero a la ubicación donde se va a colocar el elemento de la matriz.

### <a name="remarks"></a>Comentarios

Esta función llama automáticamente a las funciones `SafeArrayLock` de `SafeArrayUnlock` Windows y antes y después de recuperar el elemento. Si el elemento de datos es una cadena, un objeto o una variante, la función copia el elemento de la manera correcta. El parámetro *pvData* debe apuntar a un búfer suficientemente grande para contener el elemento.

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

Recupera el tamaño de un elemento de un `COleSafeArray` objeto.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Valor devuelto

Tamaño, en bytes, de los elementos de una matriz segura.

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

Devuelve el límite inferior para cualquier dimensión de un `COleSafeArray` objeto.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parámetros

*dwDim*<br/>
La dimensión de la matriz para la que se va a obtener el límite inferior.

*pLBound*<br/>
Puntero a la ubicación en la que se va a devolver el límite inferior.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

Devuelve el número de elementos de un objeto unidimensional `COleSafeArray` .

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz segura unidimensional.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray:: CreateOneDim](#createonedim).

##  <a name="getubound"></a>  COleSafeArray::GetUBound

Devuelve el límite superior de cualquier dimensión de una matriz segura.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parámetros

*dwDim*<br/>
La dimensión de la matriz para la que se va a obtener el límite superior.

*pUBound*<br/>
Puntero a la ubicación en la que se va a devolver el límite superior.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

Incrementa el recuento de bloqueos de una matriz y coloca un puntero a los datos de la matriz en el descriptor de la matriz.

```
void Lock();
```

### <a name="remarks"></a>Comentarios

En el error, produce una excepción [COleException](../../mfc/reference/coleexception-class.md).

El puntero en el descriptor de matriz `Unlock` es válido hasta que se llama a. Las llamadas `Lock` a se pueden anidar; se requiere un número igual `Unlock` de llamadas a.

No se puede eliminar una matriz mientras está bloqueada.

##  <a name="operator_lpcvariant"></a>COleSafeArray:: Operator LPCVARIANT

Llame a este operador de conversión para tener `VARIANT` acceso a la `COleSafeArray` estructura subyacente de este objeto.

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>COleSafeArray:: Operator LPVARIANT

Llame a este operador de conversión para tener `VARIANT` acceso a la `COleSafeArray` estructura subyacente de este objeto.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Comentarios

Tenga en cuenta que al cambiar el `VARIANT` valor de la estructura a la que accede el puntero devuelto por esta función, `COleSafeArray` cambiará el valor de este objeto.

##  <a name="operator_eq"></a>COleSafeArray:: Operator =

Estos operadores de asignación sobrecargados copian el valor de `COleSafeArray` origen en este objeto.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Comentarios

A continuación se muestra una breve descripción de cada operador:

- **Operator = (** *saSrc* **)** Copia un objeto `COleSafeArray` existente en este objeto.

- **Operator = (** *varSrc* **)** Copia una matriz `VARIANT` existente `COleVariant` o en este objeto.

- **Operator = (** *pSrc* **)** Copia el `VARIANT` objeto de matriz al que tiene acceso *pSrc* en este objeto.

##  <a name="operator_eq_eq"></a>COleSafeArray:: Operator = =

Este operador`SAFEARRAY`compara dos matrices ( `VARIANT` `COleVariant`matrices,, o `COleSafeArray` ) y devuelve un valor distinto de cero si son iguales; de lo contrario, es 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Comentarios

Dos matrices son iguales si tienen el mismo número de dimensiones, el mismo tamaño en cada dimensión y los mismos valores de elemento.

##  <a name="operator_lt_lt"></a>COleSafeArray:: Operator&lt;&lt;

El `COleSafeArray` operador de inserción (< <) admite el volcado de diagnóstico y `COleSafeArray` el almacenamiento de un objeto en un archivo.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>COleSafeArray::P trOfIndex

Devuelve un puntero al elemento especificado por los valores de índice.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Matriz de valores de índice que identifican un elemento de la matriz. Se deben especificar todos los índices del elemento.

*ppvData*<br/>
En la devolución, puntero al elemento identificado por los valores de *rgIndices*.

##  <a name="putelement"></a>  COleSafeArray::PutElement

Asigna un único elemento en la matriz.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Puntero a una matriz de índices para cada dimensión de la matriz.

*pvData*<br/>
Puntero a los datos que se va a asignar a la matriz. Los tipos de variante VT_DISPATCH, VT_UNKNOWN y VT_BSTR son punteros y no requieren otro nivel de direccionamiento indirecto.

### <a name="remarks"></a>Comentarios

Esta función llama automáticamente a las funciones de Windows [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) y [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) antes y después de asignar el elemento. Si el elemento de datos es una cadena, un objeto o una variante, la función lo copia correctamente y si el elemento existente es una cadena, un objeto o una variante, se borra correctamente.

Tenga en cuenta que puede tener múltiples bloqueos en una matriz, por lo que puede colocar elementos en una matriz, mientras que la matriz está bloqueada por otras operaciones.

En el error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

Cambia el límite menos significativo (derecho) de una matriz segura.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parámetros

*psaboundNew*<br/>
Puntero a una nueva estructura de enlace de matriz segura que contiene la nueva matriz enlazada. Solo se puede cambiar la dimensión menos significativa de una matriz.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

Cambia el número de elementos de un objeto unidimensional `COleSafeArray` .

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parámetros

*dwElements*<br/>
Número de elementos de la matriz segura unidimensional.

### <a name="remarks"></a>Comentarios

En el error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray:: CreateOneDim](#createonedim).

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

Disminuye el recuento de bloqueos de una matriz e invalida el puntero recuperado `AccessData`por.

```
void UnaccessData();
```

### <a name="remarks"></a>Comentarios

En el error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray:: AccessData](#accessdata).

##  <a name="unlock"></a>  COleSafeArray::Unlock

Disminuye el recuento de bloqueos de una matriz para que se pueda liberar o cambiar de tamaño.

```
void Unlock();
```

### <a name="remarks"></a>Comentarios

Se llama a esta función después de que haya finalizado el acceso a los datos de una matriz. En el error, produce una excepción [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
