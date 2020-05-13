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
ms.openlocfilehash: 10e9975bac776429a38bfc707215a9465ce35c2e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753773"
---
# <a name="colesafearray-class"></a>Clase COleSafeArray

Una clase para trabajar con matrices de tipo y dimensión arbitrarios.

## <a name="syntax"></a>Sintaxis

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Construye un objeto `COleSafeArray`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Recupera un puntero a los datos de la matriz.|
|[COleSafeArray::AllocData](#allocdata)|Asigna memoria para la matriz.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Asigna memoria para el descriptor de matriz segura.|
|[COleSafeArray::Attach](#attach)|Proporciona el control `VARIANT` de `COleSafeArray` la matriz existente al objeto.|
|[COleSafeArray::Clear](#clear)|Libera todos los datos `VARIANT`del archivo .|
|[COleSafeArray::Copy](#copy)|Crea una copia de una matriz existente.|
|[COleSafeArray::Crear](#create)|Crea una matriz segura.|
|[COleSafeArray::CreateOneDim](#createonedim)|Crea un objeto `COleSafeArray` unidimensional.|
|[COleSafeArray::Destroy](#destroy)|Destruye una matriz existente.|
|[COleSafeArray::DestroyData](#destroydata)|Destruye datos en una matriz segura.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Destruye un descriptor de una matriz segura.|
|[COleSafeArray::Detach](#detach)|Separa la matriz VARIANT `COleSafeArray` del objeto (para que los datos no se liberen).|
|[COleSafeArray::GetByteArray](#getbytearray)|Copia el contenido de la matriz segura en un [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Devuelve el número de dimensiones de la matriz.|
|[COleSafeArray::GetElement](#getelement)|Recupera un único elemento de la matriz segura.|
|[COleSafeArray::GetElemSize](#getelemsize)|Devuelve el tamaño, en bytes, de un elemento de una matriz segura.|
|[COleSafeArray::GetLBound](#getlbound)|Devuelve el límite inferior para cualquier dimensión de una matriz segura.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Devuelve el número de elementos `COleSafeArray` del objeto unidimensional.|
|[COleSafeArray::GetUBound](#getubound)|Devuelve el límite superior de cualquier dimensión de una matriz segura.|
|[COleSafeArray::Lock](#lock)|Incrementa el recuento de bloqueos de una matriz y coloca un puntero a los datos de la matriz en el descriptor de matriz.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Devuelve un puntero al elemento indizado.|
|[COleSafeArray::PutElement](#putelement)|Asigna un único elemento en la matriz.|
|[COleSafeArray::Redim](#redim)|Cambia el límite menos significativo (más a la derecha) de una matriz segura.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Cambia el número de elementos `COleSafeArray` de un objeto unidimensional.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Disminuye el recuento de bloqueos de una matriz e `AccessData`invalida el puntero recuperado por .|
|[COleSafeArray::Unlock](#unlock)|Disminuye el recuento de bloqueos de una matriz para que se pueda liberar o cambiar de tamaño.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleSafeArray::operador LPCVARIANT](#operator_lpcvariant)|Tiene acceso a `VARIANT` la `COleSafeArray` estructura subyacente del objeto.|
|[COleSafeArray::operador LPVARIANT](#operator_lpvariant)|Tiene acceso a `VARIANT` la `COleSafeArray` estructura subyacente del objeto.|
|[COleSafeArray::operador ?](#operator_eq)|Copia los `COleSafeArray` valores`SAFEARRAY`en `VARIANT` `COleVariant`un `COleSafeArray` objeto ( , , , o matriz).|
|[COleSafeArray::operador ?](#operator_eq_eq)|Compara dos matrices`SAFEARRAY`de `VARIANT` `COleVariant`variantes `COleSafeArray` ( , , , o matrices).|
|[COleSafeArray::operator&lt;&lt;](#operator_lt_lt)|Produce el contenido `COleSafeArray` de un objeto en el contexto de volcado.|

## <a name="remarks"></a>Observaciones

`COleSafeArray`deriva de la `VARIANT` estructura OLE. Las `SAFEARRAY` funciones miembro `COleSafeArray`OLE están disponibles a través de , así como un conjunto de funciones miembro diseñadas específicamente para matrices unidimensionales de bytes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::AccessData

Recupera un puntero a los datos de la matriz.

```cpp
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parámetros

*ppvData*<br/>
Puntero a un puntero a los datos de la matriz.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData

Asigna memoria para una matriz segura.

```cpp
void AllocData();
```

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor

Asigna memoria para el descriptor de una matriz segura.

```cpp
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parámetros

*dwDims*<br/>
Número de dimensiones en la matriz segura.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Attach

Proporciona el control de `VARIANT` los datos `COleSafeArray` de una matriz existente al objeto.

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Objeto `VARIANT` . El parámetro *varSrc* debe tener el [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)VARTYPE .

### <a name="remarks"></a>Observaciones

El `VARIANT`tipo de origen se establece en VT_EMPTY. Esta función borra los datos de la matriz actual, si los hay.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Clear

Borra la matriz segura.

```cpp
void Clear();
```

### <a name="remarks"></a>Observaciones

La función borra una matriz `VARTYPE` segura estableciendo el objeto en VT_EMPTY. El contenido actual se libera y la matriz se libera.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray

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
Un `COleSafeArray` objeto `SAFEARRAY` existente o que se `COleSafeArray` va a copiar en el nuevo objeto.

*vtSrc*<br/>
El VARTYPE del `COleSafeArray` nuevo objeto.

*psaSrc*<br/>
Puntero a `SAFEARRAY` a que se va `COleSafeArray` a copiar en el nuevo objeto.

*varSrc*<br/>
Un `VARIANT` objeto `COleVariant` u objeto existente que `COleSafeArray` se va a copiar en el nuevo objeto.

*pSrc*<br/>
Puntero a `VARIANT` un objeto que se `COleSafeArray` va a copiar en el nuevo objeto.

### <a name="remarks"></a>Observaciones

Todos estos constructores `COleSafeArray` crean nuevos objetos. Si no hay ningún `COleSafeArray` parámetro, se crea un objeto vacío (VT_EMPTY). Si `COleSafeArray` se copia desde otra matriz cuyo VARTYPE `COleSafeArray`se `COleVariant`conoce `VARIANT`implícitamente (a , , o ), el VARTYPE de la matriz de origen se conserva y no es necesario especificarlo. Si `COleSafeArray` se copia desde otra matriz cuyo VARTYPE no se conoce (`SAFEARRAY`), el VARTYPE debe especificarse en el parámetro *vtSrc.*

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Copy

Crea una copia de una matriz segura existente.

```cpp
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parámetros

*Ppsa*<br/>
Puntero a una ubicación en la que se va a devolver el nuevo descriptor de matriz.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafeArray::Crear

Asigna e inicializa los datos de la matriz.

```cpp
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
El tipo base de la matriz (es decir, el VARTYPE de cada elemento de la matriz). El VARTYPE está restringido a un subconjunto de los tipos de variante. No se puede establecer ni el VT_ARRAY ni el indicador VT_BYREF. VT_EMPTY y VT_NULL no son tipos base válidos para la matriz. Todos los demás tipos son legales.

*dwDims*<br/>
Número de dimensiones de la matriz. Esto se puede cambiar después de crear la matriz con [Redim](#redim).

*rgElements*<br/>
Puntero a una matriz del número de elementos para cada dimensión de la matriz.

*rgsabounds*<br/>
Puntero a un vector de límites (uno para cada dimensión) para asignar para la matriz.

### <a name="remarks"></a>Observaciones

Esta función borrará los datos de la matriz actual si es necesario. En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim

Crea un nuevo `COleSafeArray` objeto unidimensional.

```cpp
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
Número de elementos de la matriz. Esto se puede cambiar después de crear la matriz con [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Puntero a los datos que se van a copiar en la matriz.

*nLBound*<br/>
El límite inferior de la matriz.

### <a name="remarks"></a>Observaciones

La función asigna e inicializa los datos de la matriz, copiando los datos especificados si el puntero *pvSrcData* no es NULL.

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy

Destruye un descriptor de matriz existente y todos los datos de la matriz.

```cpp
void Destroy();
```

### <a name="remarks"></a>Observaciones

Si los objetos se almacenan en la matriz, se libera cada objeto. En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData

Destruye todos los datos de una matriz segura.

```cpp
void DestroyData();
```

### <a name="remarks"></a>Observaciones

Si los objetos se almacenan en la matriz, se libera cada objeto. En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor

Destruye un descriptor de una matriz segura.

```cpp
void DestroyDescriptor();
```

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach

Separa los `VARIANT` datos `COleSafeArray` del objeto.

```
VARIANT Detach();
```

### <a name="return-value"></a>Valor devuelto

El valor `VARIANT` subyacente `COleSafeArray` del objeto.

### <a name="remarks"></a>Observaciones

La función separa los datos de una matriz segura estableciendo el VARTYPE del objeto en VT_EMPTY. Es responsabilidad del autor de la llamada liberar la matriz llamando a la función de Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

En caso de error, la función produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::PutElement](#putelement).

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray

Copia el contenido de la `CByteArray`matriz segura en un archivo .

```cpp
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parámetros

*Bytes*<br/>
Una referencia a un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto.

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim

Devuelve el número de `COleSafeArray` dimensiones del objeto.

```
DWORD GetDim();
```

### <a name="return-value"></a>Valor devuelto

El número de dimensiones de la matriz segura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement

Recupera un único elemento de la matriz segura.

```cpp
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Puntero a una matriz de índices para cada dimensión de la matriz.

*pvData*<br/>
Puntero a la ubicación para colocar el elemento de la matriz.

### <a name="remarks"></a>Observaciones

Esta función llama `SafeArrayLock` automáticamente `SafeArrayUnlock` a las funciones de Windows y antes y después de recuperar el elemento. Si el elemento de datos es una cadena, objeto o variante, la función copia el elemento de la manera correcta. El parámetro *pvData* debe apuntar a un búfer lo suficientemente grande como para contener el elemento.

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize

Recupera el tamaño de un `COleSafeArray` elemento de un objeto.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Valor devuelto

El tamaño, en bytes, de los elementos de una matriz segura.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLBound

Devuelve el límite inferior para `COleSafeArray` cualquier dimensión de un objeto.

```cpp
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parámetros

*dwDim*<br/>
La dimensión de matriz para la que se obtiene el límite inferior.

*pLBound*<br/>
Puntero a la ubicación para devolver el límite inferior.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetOneDimSize

Devuelve el número de elementos `COleSafeArray` del objeto unidimensional.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de la matriz segura unidimensional.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::GetUBound

Devuelve el límite superior de cualquier dimensión de una matriz segura.

```cpp
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parámetros

*dwDim*<br/>
La dimensión de matriz para la que se obtiene el límite superior.

*pUBound*<br/>
Puntero a la ubicación para devolver el límite superior.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafeArray::Lock

Incrementa el recuento de bloqueos de una matriz y coloca un puntero a los datos de la matriz en el descriptor de matriz.

```cpp
void Lock();
```

### <a name="remarks"></a>Observaciones

En error, se produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

El puntero en el descriptor `Unlock` de matriz es válido hasta que se llama. Las `Lock` llamadas a se pueden anidar; se requiere un `Unlock` número igual de llamadas.

Una matriz no se puede eliminar mientras está bloqueada.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::operador LPCVARIANT

Llame a este operador de `VARIANT` conversión `COleSafeArray` para tener acceso a la estructura subyacente de este objeto.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::operador LPVARIANT

Llame a este operador de `VARIANT` conversión `COleSafeArray` para tener acceso a la estructura subyacente de este objeto.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Observaciones

Tenga en cuenta que `VARIANT` cambiar el valor de la estructura a `COleSafeArray` la que tiene acceso el puntero devuelto por esta función cambiará el valor de este objeto.

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::operador ?

Estos operadores de asignación sobrecargados copian el valor de origen en este `COleSafeArray` objeto.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Observaciones

A continuación se ofrece una breve descripción de cada operador:

- **operador (** *saSrc* **)** Copia un `COleSafeArray` objeto existente en este objeto.

- **operador (** *varSrc* **)** Copia una `VARIANT` `COleVariant` matriz o existente en este objeto.

- **Operador** *(pSrc* **)** Copia `VARIANT` el objeto de matriz al que tiene acceso *pSrc* en este objeto.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::operador ?

Este operador compara dos`SAFEARRAY`matrices `COleVariant`( `COleSafeArray` , `VARIANT`, , o matrices) y devuelve distinto de cero si son iguales; de lo contrario 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Observaciones

Dos matrices son iguales si tienen un número igual de dimensiones, el mismo tamaño en cada dimensión y valores de elemento igual.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray::operator&lt;&lt;

El `COleSafeArray` operador de inserción (<<) admite `COleSafeArray` el volcado de diagnóstico y el almacenamiento de un objeto en un archivo.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafeArray::PtrOfIndex

Devuelve un puntero al elemento especificado por los valores de índice.

```cpp
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Matriz de valores de índice que identifican un elemento de la matriz. Se deben especificar todos los índices del elemento.

*ppvData*<br/>
Al volver, puntero al elemento identificado por los valores de *rgIndices*.

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafeArray::PutElement

Asigna un único elemento en la matriz.

```cpp
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Puntero a una matriz de índices para cada dimensión de la matriz.

*pvData*<br/>
Puntero a los datos que se va a asignar a la matriz. VT_DISPATCH, VT_UNKNOWN y VT_BSTR tipos de variantes son punteros y no requieren otro nivel de direccionamiento indirecto.

### <a name="remarks"></a>Observaciones

Esta función llama automáticamente a las funciones de Windows [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) y [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) antes y después de asignar el elemento. Si el elemento de datos es una cadena, un objeto o una variante, la función lo copia correctamente y si el elemento existente es una cadena, un objeto o una variante, se borra correctamente.

Tenga en cuenta que puede tener múltiples bloqueos en una matriz, por lo que puede colocar elementos en una matriz, mientras que la matriz está bloqueada por otras operaciones.

En caso de error, la función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafeArray::Redim

Cambia el límite menos significativo (más a la derecha) de una matriz segura.

```cpp
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parámetros

*psaboundNew*<br/>
Puntero a una nueva estructura enlazada a una matriz segura que contiene el nuevo enlazado de matriz. Solo se puede cambiar la dimensión menos significativa de una matriz.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafeArray::ResizeOneDim

Cambia el número de elementos `COleSafeArray` de un objeto unidimensional.

```cpp
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parámetros

*dwElements*<br/>
Número de elementos de la matriz segura unidimensional.

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafeArray::UnaccessData

Disminuye el recuento de bloqueos de una matriz e `AccessData`invalida el puntero recuperado por .

```cpp
void UnaccessData();
```

### <a name="remarks"></a>Observaciones

En caso de error, la función produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafeArray::Unlock

Disminuye el recuento de bloqueos de una matriz para que se pueda liberar o cambiar de tamaño.

```cpp
void Unlock();
```

### <a name="remarks"></a>Observaciones

Se llama a esta función una vez finalizado el acceso a los datos de una matriz. En error, se produce una [excepción COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Clase CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
