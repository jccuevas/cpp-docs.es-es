---
title: COleSafeArray (clase) | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1bad1ccc1671176ce213e59c5d4c8c318a441b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203429"
---
# <a name="colesafearray-class"></a>COleSafeArray (clase)
Una clase para trabajar con matrices de tipo y dimensión arbitrarios.

## <a name="syntax"></a>Sintaxis

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Construye un objeto `COleSafeArray`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Recupera un puntero a los datos de matriz.|
|[COleSafeArray::AllocData](#allocdata)|Asigna memoria para la matriz.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Asigna memoria para el descriptor de matriz segura.|
|[COleSafeArray::Attach](#attach)|Proporciona control de la existente `VARIANT` de matriz a la `COleSafeArray` objeto.|
|[COleSafeArray::Clear](#clear)|Libera todos los datos en subyacente `VARIANT`.|
|[COleSafeArray::Copy](#copy)|Crea una copia de una matriz existente.|
|[COleSafeArray::Create](#create)|Crea una matriz segura.|
|[COleSafeArray::CreateOneDim](#createonedim)|Crea un unidimensional `COleSafeArray` objeto.|
|[COleSafeArray::Destroy](#destroy)|Destruye una matriz existente.|
|[COleSafeArray::DestroyData](#destroydata)|Destruye los datos en una matriz segura.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Destruye un descriptor de la matriz segura.|
|[COleSafeArray::Detach](#detach)|Desasocia la matriz de tipo VARIANT de la `COleSafeArray` objeto (de modo que no se liberarán los datos).|
|[COleSafeArray::GetByteArray](#getbytearray)|Copia el contenido de la matriz segura en un [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Devuelve el número de dimensiones de la matriz.|
|[Colesafearray:: GetElement](#getelement)|Recupera un único elemento de la matriz segura.|
|[COleSafeArray::GetElemSize](#getelemsize)|Devuelve el tamaño, en bytes, de un elemento en una matriz segura.|
|[COleSafeArray::GetLBound](#getlbound)|Devuelve el límite inferior de cualquier dimensión de una matriz segura.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Devuelve el número de elementos de unidimensional `COleSafeArray` objeto.|
|[COleSafeArray::GetUBound](#getubound)|Devuelve el límite superior de cualquier dimensión de una matriz segura.|
|[COleSafeArray::Lock](#lock)|Incrementa el recuento de bloqueos de una matriz y coloca un puntero a los datos de matriz en el descriptor de matriz.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Devuelve un puntero al elemento indizado.|
|[COleSafeArray::PutElement](#putelement)|Asigna un único elemento en la matriz.|
|[COleSafeArray::Redim](#redim)|Cambia el límite menos significativo (derecho) de una matriz segura.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Cambia el número de elementos de unidimensional `COleSafeArray` objeto.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Disminuye el bloqueo del contador de una matriz e invalida el puntero recuperado por `AccessData`.|
|[COleSafeArray::Unlock](#unlock)|Reduce el recuento de bloqueos de la matriz por lo que se puede liberar o cambiar de tamaño.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Tiene acceso a subyacente `VARIANT` estructura de la `COleSafeArray` objeto.|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Tiene acceso a subyacente `VARIANT` estructura de la `COleSafeArray` objeto.|
|[COleSafeArray::operator =](#operator_eq)|Copia los valores en un `COleSafeArray` objeto (`SAFEARRAY`, `VARIANT`, `COleVariant`, o `COleSafeArray` matriz).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Compara dos matrices variantes (`SAFEARRAY`, `VARIANT`, `COleVariant`, o `COleSafeArray` matrices).|
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|Envía el contenido de un `COleSafeArray` objeto en el contexto de volcado.|

## <a name="remarks"></a>Comentarios

`COleSafeArray` se deriva de OLE `VARIANT` estructura. OLE `SAFEARRAY` están disponibles a través de las funciones miembro `COleSafeArray`, así como un conjunto de funciones miembro diseñado específicamente para las matrices unidimensionales de bytes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

Recupera un puntero a los datos de matriz.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parámetros

*ppvData*<br/>
Un puntero a un puntero a los datos de matriz.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

Asigna memoria para una matriz segura.

```
void AllocData();
```

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

Asigna memoria para el descriptor de una matriz segura.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parámetros

*dwDims*<br/>
Número de dimensiones de la matriz segura.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="attach"></a>  COleSafeArray::Attach

Proporciona control de los datos en una existente `VARIANT` de matriz a la `COleSafeArray` objeto.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parámetros

*varSrc*<br/>
Un objeto `VARIANT`. El *varSrc* parámetro debe tener el valor de VARTYPE [VT_ARRAY](/windows/desktop/api/wtypes/ne-wtypes-varenum).

### <a name="remarks"></a>Comentarios

El origen `VARIANT`del tipo está establecido en VT_EMPTY. Esta función borra los datos de la matriz actual, si existe.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::AccessData](#accessdata).

##  <a name="clear"></a>  COleSafeArray::Clear

Borra la matriz segura.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

La función borra una matriz segura estableciendo el `VARTYPE` del objeto en VT_EMPTY. El contenido actual se libera y se libera la matriz.

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
Existente `COleSafeArray` objeto o `SAFEARRAY` va a copiar en el nuevo `COleSafeArray` objeto.

*vtSrc*<br/>
El valor de VARTYPE nuevo `COleSafeArray` objeto.

*psaSrc*<br/>
Un puntero a un `SAFEARRAY` va a copiar en el nuevo `COleSafeArray` objeto.

*varSrc*<br/>
Existente `VARIANT` o `COleVariant` objeto que se copiará en el nuevo `COleSafeArray` objeto.

*pSrc*<br/>
Un puntero a un `VARIANT` objeto que se copiará en el nuevo `COleSafeArray` objeto.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleSafeArray` objetos. Si no hay ningún parámetro, un valor vacío `COleSafeArray` se crea el objeto (VT_EMPTY). Si el `COleSafeArray` se copian desde otra matriz cuyo VARTYPE se conoce de forma implícita (un `COleSafeArray`, `COleVariant`, o `VARIANT`), el valor de VARTYPE la matriz de origen se conserva y no es necesario especificar. Si el `COleSafeArray` se copian desde otra matriz cuyo VARTYPE no se conoce (`SAFEARRAY`), el valor de VARTYPE debe especificarse en el *vtSrc* parámetro.

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="copy"></a>  COleSafeArray::Copy

Crea una copia de una matriz segura existente.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parámetros

*ppsa*<br/>
Puntero a una ubicación en la que se va a devolver el nuevo descriptor de matriz.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

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
El tipo base de la matriz (es decir, el valor de VARTYPE cada elemento de la matriz). El valor de VARTYPE está restringido a un subconjunto de los tipos variantes. Se puede establecer el VT_ARRAY ni la marca VT_BYREF. VT_EMPTY y VT_NULL no son tipos base válidos para la matriz. Todos los demás tipos son válidos.

*dwDims*<br/>
Número de dimensiones de la matriz. Esto se puede cambiar después de la matriz se crea con [Redim](#redim).

*rgElements*<br/>
Puntero a una matriz del número de elementos para cada dimensión de la matriz.

*rgsabounds*<br/>
Puntero a un vector de límites (uno para cada dimensión) para asignar para la matriz.

### <a name="remarks"></a>Comentarios

Esta función borrará los datos actuales de la matriz si es necesario. En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

Crea un nuevo unidimensional `COleSafeArray` objeto.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parámetros

*vtSrc*<br/>
El tipo base de la matriz (es decir, el valor de VARTYPE cada elemento de la matriz).

*dwElements*<br/>
Número de elementos de la matriz. Esto se puede cambiar después de la matriz se crea con [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Puntero a los datos que se va a copiar en la matriz.

*nLBound*<br/>
El límite inferior de la matriz.

### <a name="remarks"></a>Comentarios

La función asigna e inicializa los datos de la matriz, copiar los datos especificados, si el puntero *pvSrcData* no es NULL.

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

Destruye un descriptor de matriz existente y todos los datos de la matriz.

```
void Destroy();
```

### <a name="remarks"></a>Comentarios

Si los objetos se almacenan en la matriz, cada objeto se liberan. En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

Destruye todos los datos en una matriz segura.

```
void DestroyData();
```

### <a name="remarks"></a>Comentarios

Si los objetos se almacenan en la matriz, cada objeto se liberan. En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

Destruye un descriptor de la matriz segura.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="detach"></a>  COleSafeArray::Detach

Desasocia el `VARIANT` datos desde el `COleSafeArray` objeto.

```
VARIANT Detach();
```

### <a name="return-value"></a>Valor devuelto

Subyacente `VARIANT` valor en el `COleSafeArray` objeto.

### <a name="remarks"></a>Comentarios

La función separa los datos en una matriz segura estableciendo el valor de VARTYPE del objeto en VT_EMPTY. Es responsabilidad del llamante liberar la matriz mediante una llamada a la función Windows [VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear).

En caso de error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::PutElement](#putelement).

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

Copia el contenido de la matriz segura en un `CByteArray`.

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parámetros

*Bytes*<br/>
Una referencia a un [CByteArray](../../mfc/reference/cbytearray-class.md) objeto.

##  <a name="getdim"></a>  COleSafeArray::GetDim

Devuelve el número de dimensiones en el `COleSafeArray` objeto.

```
DWORD GetDim();
```

### <a name="return-value"></a>Valor devuelto

El número de dimensiones de la matriz segura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  Colesafearray:: GetElement

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
Puntero a la ubicación para colocar el elemento de la matriz.

### <a name="remarks"></a>Comentarios

Esta función llama automáticamente a las funciones de windows `SafeArrayLock` y `SafeArrayUnlock` antes y después de recuperar el elemento. Si el elemento de datos es una cadena, un objeto o una variante, la función copia el elemento de la manera correcta. El parámetro *pvData* debe apuntar a un gran suficiente búfer para que contenga el elemento.

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

Recupera el tamaño de un elemento en un `COleSafeArray` objeto.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Valor devuelto

El tamaño, en bytes, de los elementos de una matriz segura.

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

Devuelve el límite inferior de cualquier dimensión de un `COleSafeArray` objeto.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parámetros

*dwDim*<br/>
La dimensión de matriz para que se va a obtener el límite inferior.

*pLBound*<br/>
Puntero a la ubicación para devolver el límite inferior.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

Devuelve el número de elementos de unidimensional `COleSafeArray` objeto.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de la matriz segura unidimensional.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="getubound"></a>  COleSafeArray::GetUBound

Devuelve el límite superior de cualquier dimensión de una matriz segura.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parámetros

*dwDim*<br/>
La dimensión de matriz para que se va a obtener el límite superior.

*pUBound*<br/>
Puntero a la ubicación para devolver el límite superior.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

Incrementa el recuento de bloqueos de una matriz y el lugar de un puntero a los datos de matriz en el descriptor de matriz.

```
void Lock();
```

### <a name="remarks"></a>Comentarios

En caso de error, produce un [COleException](../../mfc/reference/coleexception-class.md).

El puntero en el descriptor de matriz es válido hasta `Unlock` se llama. Las llamadas a `Lock` se pueden anidar; un número igual de llamadas a `Unlock` son necesarios.

Una matriz no puede eliminarse aunque esté bloqueado.

##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT

Llamar a este operador de conversión para obtener acceso a subyacente `VARIANT` estructura para este `COleSafeArray` objeto.

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT

Llamar a este operador de conversión para obtener acceso a subyacente `VARIANT` estructura para este `COleSafeArray` objeto.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Comentarios

Tenga en cuenta que al cambiar el valor de la `VARIANT` estructura accediendo el puntero devuelto por esta función cambiará el valor de esta `COleSafeArray` objeto.

##  <a name="operator_eq"></a>  COleSafeArray::operator =

Estos operadores de asignaciones sobrecargados copian el valor de origen en este `COleSafeArray` objeto.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Comentarios

A continuación se muestra una breve descripción de cada operador:

- **operador = (** *saSrc* **)** copia existente `COleSafeArray` objeto en este objeto.

- **operador = (** *varSrc* **)** copia existente `VARIANT` o `COleVariant` matriz en este objeto.

- **operador = (** *pSrc* **)** copias el `VARIANT` objeto array accediendo a *pSrc* en este objeto.

##  <a name="operator_eq_eq"></a>  COleSafeArray::operator ==

Este operador compara dos matrices (`SAFEARRAY`, `VARIANT`, `COleVariant`, o `COleSafeArray` matrices) y devuelve cero si son iguales; de lo contrario, 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Comentarios

Dos matrices son iguales si tienen el mismo número de dimensiones, el mismo tamaño de cada dimensión y los valores de elementos iguales.

##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;

El `COleSafeArray` inserción (<<) admite el operador volcado de diagnóstico y almacenamiento de un `COleSafeArray` objeto en un archivo.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex

Devuelve un puntero al elemento especificado por los valores de índice.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parámetros

*rgIndices*<br/>
Una matriz de valores de índice que identifican un elemento de la matriz. Se deben especificar todos los índices del elemento.

*ppvData*<br/>
En el puntero devuelto, el elemento identificado por los valores de *rgIndices*.

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
Puntero a los datos que se va a asignar a la matriz. VT_BSTR, VT_UNKNOWN y VT_DISPATCH tipos variant son punteros y no requieren otro nivel de direccionamiento indirecto.

### <a name="remarks"></a>Comentarios

Esta función llama automáticamente a las funciones de Windows [SafeArrayLock](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraylock) y [SafeArrayUnlock](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearrayunlock) antes y después de asignar el elemento. Si el elemento de datos es una cadena, un objeto o una variante, la función lo copia correctamente y si el elemento existente es una cadena, un objeto o una variante, se borra correctamente.

Tenga en cuenta que puede tener múltiples bloqueos en una matriz, por lo que puede colocar elementos en una matriz, mientras que la matriz está bloqueada por otras operaciones.

En caso de error, la función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) o [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

Cambia el límite menos significativo (derecho) de una matriz segura.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parámetros

*psaboundNew*<br/>
Puntero a una nueva matriz segura enlazado estructura que contiene la nueva matriz dependiente. Se puede cambiar sólo la dimensión menos significativa de la matriz.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

Cambia el número de elementos de unidimensional `COleSafeArray` objeto.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parámetros

*dwElements*<br/>
Número de elementos de la matriz segura unidimensional.

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

Disminuye el bloqueo del contador de una matriz e invalida el puntero recuperado por `AccessData`.

```
void UnaccessData();
```

### <a name="remarks"></a>Comentarios

En caso de error, la función produce un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [COleSafeArray::AccessData](#accessdata).

##  <a name="unlock"></a>  COleSafeArray::Unlock

Reduce el recuento de bloqueos de la matriz por lo que se puede liberar o cambiar de tamaño.

```
void Unlock();
```

### <a name="remarks"></a>Comentarios

Esta función se llama una vez finalizado la acceso a los datos en una matriz. En caso de error, produce un [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
