---
title: CComSafeArray (clase)
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327400"
---
# <a name="ccomsafearray-class"></a>CComSafeArray (clase)

Esta clase es un `SAFEARRAY` contenedor para la estructura.

## <a name="syntax"></a>Sintaxis

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo de datos que se va a almacenar en la matriz.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|El constructor.|
|[CComSafeArray::-CComSafeArray](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSafeArray::Add](#add)|Agrega uno o más elementos, o una `SAFEARRAY` estructura, a un `CComSafeArray`archivo .|
|[CComSafeArray::Attach](#attach)|Asocia una `SAFEARRAY` estructura `CComSafeArray` a un objeto.|
|[CComSafeArray::CopyFrom](#copyfrom)|Copia el contenido `SAFEARRAY` de `CComSafeArray` una estructura en el objeto.|
|[CComSafeArray::CopyTo](#copyto)|Crea una copia del objeto `CComSafeArray` .|
|[CComSafeArray::Create](#create)|Crea un objeto `CComSafeArray` .|
|[CComSafeArray::Destroy](#destroy)|Destruye un objeto `CComSafeArray` .|
|[CComSafeArray::Detach](#detach)|Separa un `SAFEARRAY` `CComSafeArray` objeto.|
|[CComSafeArray::GetAt](#getat)|Recupera un único elemento de una matriz unidimensional.|
|[CComSafeArray::GetCount](#getcount)|Devuelve el número de elementos de la matriz.|
|[CComSafeArray::GetDimensions](#getdimensions)|Devuelve el número de dimensiones de la matriz.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Devuelve el límite inferior de una determinada dimensión de la matriz.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Devuelve la dirección del miembro de datos `m_psa` .|
|[CComSafeArray::GetType](#gettype)|Devuelve el tipo de datos almacenado en la matriz.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Devuelve el límite superior de cualquier dimensión de la matriz.|
|[CComSafeArray::IsSizable](#issizable)|Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .|
|[CComsafeArray::MultidimgetAt](#multidimgetat)|Recupera un único elemento de una matriz multidimensional.|
|[CComSafeArray::MultidimSetAt](#multidimsetat)|Establece el valor de un elemento de una matriz multidimensional.|
|[CComSafeArray::Resize](#resize)|Cambia el tamaño de un objeto `CComSafeArray` .|
|[CComSafeArray::SetAt](#setat)|Establece el valor de un elemento de una matriz unidimensional.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSafeArray::operador LPSAFEARRAY](#operator_lpsafearray)|Convierte un valor `SAFEARRAY` en un puntero.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Recupera un elemento de la matriz.|
|[CComSafeArray::operator ?](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Este miembro de datos contiene `SAFEARRAY` la dirección de la estructura.|

## <a name="remarks"></a>Observaciones

`CComSafeArray` proporciona un contenedor para la clase [SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray) , lo que facilita la creación y administración de matrices unidimensionales y multidimensionales de casi cualquiera de los tipos compatibles VARIANT.

`CComSafeArray` simplifica el paso de matrices entre procesos y, además, proporciona seguridad adicional al comprobar los valores de índice de matriz con los limites superior e inferior.

El límite inferior de `CComSafeArray` puede empezar por cualquier valor definido por el usuario, pero las matrices a las que se accede a través de C++ usan un límite inferior de 0. Otros lenguajes como Visual Basic pueden usar otros valores límite (por ejemplo, de -10 a 10).

Use [CComSafeArray::Create](#create) para crear un objeto `CComSafeArray` y [CComSafeArray::Destroy](#destroy) para eliminarlo.

Un elemento `CComSafeArray` puede contener el siguiente subconjunto de tipos de datos VARIANT:

|VARTYPE|Descripción|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|FLOAT|
|VT_R8|double|
|VT_DECIMAL|puntero decimal|
|VT_VARIANT|puntero variant|
|VT_CY|Currency (tipo de datos)|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsafe.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafeArray::Add

Agrega uno o más elementos, o una `SAFEARRAY` estructura, a un `CComSafeArray`archivo .

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parámetros

*psaSrc*<br/>
Puntero a un objeto `SAFEARRAY` .

*ulCount*<br/>
El número de objetos que se va a agregar a la matriz.

*Pt*<br/>
Puntero a uno o varios objetos que se van a agregar a la matriz.

*T*<br/>
Una referencia al objeto que se va a agregar a la matriz.

*bCopy*<br/>
Indica si se debe crear una copia de los datos. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Los nuevos objetos se anexan `SAFEARRAY` al final del objeto existente. No se admite `SAFEARRAY` la adición de un objeto a un objeto multidimensional. Al agregar una matriz existente de objetos, ambas matrices deben contener elementos del mismo tipo.

El indicador *bCopy* se tiene en cuenta cuando se agregan elementos de tipo BSTR o VARIANT a una matriz. El valor predeterminado de TRUE garantiza que se realiza una nueva copia de los datos cuando se agrega el elemento a la matriz.

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafeArray::Attach

Asocia una `SAFEARRAY` estructura `CComSafeArray` a un objeto.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parámetros

*psaSrc*<br/>
Un puntero `SAFEARRAY` a la estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Asocia una `SAFEARRAY` estructura `CComSafeArray` a un objeto, haciendo que los métodos existentes `CComSafeArray` estén disponibles.

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafeArray::CComSafeArray

El constructor.

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parámetros

*Límite*<br/>
Un estructura `SAFEARRAYBOUND`.

*ulCount*<br/>
Número de elementos de la matriz.

*LLBound*<br/>
El valor límite inferior; es decir, el índice del primer elemento de la matriz.

*pBound*<br/>
Un puntero `SAFEARRAYBOUND` a una estructura.

*uDims*<br/>
El recuento de dimensiones en la matriz.

*saSrc*<br/>
Una referencia `SAFEARRAY` a `CComSafeArray` una estructura u objeto. En cualquier caso, el constructor utiliza esta referencia para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.

*psaSrc*<br/>
Un puntero `SAFEARRAY` a una estructura. El constructor utiliza esta dirección para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.

### <a name="remarks"></a>Observaciones

Crea un objeto `CComSafeArray` .

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafeArray::-CComSafeArray

Destructor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafeArray::CopyFrom

Copia el contenido `SAFEARRAY` de `CComSafeArray` una estructura en el objeto.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
Puntero a `SAFEARRAY` la copia.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método copia el `SAFEARRAY` contenido `CComSafeArray` de a en el objeto actual. Se reemplaza el contenido existente de la matriz.

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafeArray::CopyTo

Crea una copia del objeto `CComSafeArray` .

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
Puntero a una ubicación en la `SAFEARRAY`que se creará el nuevo archivo .

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método copia el `CComSafeArray` contenido `SAFEARRAY` de un objeto en una estructura.

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafeArray::Crear

Crea una interfaz `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parámetros

*pBound*<br/>
Puntero a un objeto `SAFEARRAYBOUND` .

*uDims*<br/>
Número de dimensiones de la matriz.

*ulCount*<br/>
Número de elementos de la matriz.

*LLBound*<br/>
El valor límite inferior; es decir, el índice del primer elemento de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Un `CComSafeArray` objeto se puede `SAFEARRAYBOUND` crear a partir de una estructura existente y el número de dimensiones, o especificando el número de elementos de la matriz y el límite inferior. Si se va a acceder a la matriz desde C++, el límite inferior debe ser 0. Otros lenguajes pueden permitir otros valores para el límite inferior (por ejemplo, Visual Basic admite matrices con elementos con un intervalo como -10 a 10).

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::Destroy

Destruye un objeto `CComSafeArray` .

```
HRESULT Destroy();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Destruye un `CComSafeArray` objeto existente y todos los datos que contiene.

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafeArray::Detach

Separa un `SAFEARRAY` `CComSafeArray` objeto.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero `SAFEARRAY` a un objeto.

### <a name="remarks"></a>Observaciones

Este método separa `SAFEARRAY` el `CComSafeArray` objeto del objeto.

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafeArray::GetAt

Recupera un único elemento de una matriz unidimensional.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parámetros

*Lindex*<br/>
El número de índice del valor de la matriz que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al elemento de matriz necesario.

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafeArray::GetCount

Devuelve el número de elementos de la matriz.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parámetros

*uDim*<br/>
La dimensión de matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos de la matriz.

### <a name="remarks"></a>Observaciones

Cuando se utiliza con una matriz multidimensional, este método devolverá el número de elementos en una dimensión específica solamente.

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafeArray::GetDimensions

Devuelve el número de dimensiones de la matriz.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de dimensiones de la matriz.

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray::GetLowerBound

Devuelve el límite inferior de una determinada dimensión de la matriz.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parámetros

*uDim*<br/>
La dimensión de matriz para la que se obtiene el límite inferior. Si se omite, el valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

Devuelve el límite inferior.

### <a name="remarks"></a>Observaciones

Si el límite inferior es 0, esto indica una matriz similar a C cuyo primer elemento es el número de elemento 0. En caso de error, por ejemplo, un argumento `AtlThrow` de dimensión no válido, este método llama con un HRESULT que describe el error.

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Devuelve la dirección del miembro de datos `m_psa` .

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la [CComSafeArray::m_psa](#m_psa) miembro de datos.

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafeArray::GetType

Devuelve el tipo de datos almacenado en la matriz.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tipo de datos almacenados en la matriz, que podría naser cualquiera de los siguientes tipos:

|VARTYPE|Descripción|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|FLOAT|
|VT_R8|double|
|VT_DECIMAL|puntero decimal|
|VT_VARIANT|puntero variant|
|VT_CY|Currency (tipo de datos)|

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafeArray::GetUpperBound

Devuelve el límite superior de cualquier dimensión de la matriz.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parámetros

*uDim*<br/>
La dimensión de matriz para la que se obtiene el límite superior. Si se omite, el valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior. Este valor es inclusivo, el índice válido máximo para esta dimensión.

### <a name="remarks"></a>Observaciones

En caso de error, por ejemplo, un argumento `AtlThrow` de dimensión no válido, este método llama con un HRESULT que describe el error.

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafeArray::IsSizable

Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .

```
bool IsSizable() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE `CComSafeArray` si se puede cambiar el tamaño de la redimensionación, FALSE si no puede.

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafeArray::m_psa

Contiene la dirección `SAFEARRAY` de la estructura a la que se accede.

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComsafeArray::MultidimgetAt

Recupera un único elemento de una matriz multidimensional.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parámetros

*alIndex*<br/>
Puntero a un vector de índices para cada dimensión de la matriz. La dimensión más a `alIndex[0]`la izquierda (más significativa) es .

*T*<br/>
Una referencia a los datos devueltos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafeArray::MultidimSetAt

Establece el valor de un elemento de una matriz multidimensional.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parámetros

*alIndex*<br/>
Puntero a un vector de índices para cada dimensión de la matriz. La dimensión más a `alIndex`la derecha (menos significativa) es [0].

*T*<br/>
Especifica el valor del nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Esta es una versión multidimensional de [CComSafeArray::SetAt](#setat).

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::operator\[\]

Recupera un elemento de la matriz.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parámetros

*lIndex, nIndex*<br/>
El número de índice del elemento necesario en la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento de matriz adecuado.

### <a name="remarks"></a>Observaciones

Realiza una función similar a [CComSafeArray::GetAt](#getat), sin embargo, este operador solo funciona con matrices unidimensionales.

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::operator ?

Operador de asignación.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parámetros

*saSrc*<br/>
Referencia a un objeto `CComSafeArray`.

*psaSrc*<br/>
Puntero a un objeto `SAFEARRAY` .

### <a name="return-value"></a>Valor devuelto

Devuelve el tipo de datos almacenado en la matriz.

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafeArray::operador LPSAFEARRAY

Convierte un valor `SAFEARRAY` en un puntero.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Valor devuelto

Convierte un valor `SAFEARRAY` en un puntero.

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafeArray::Resize

Cambia el tamaño de un objeto `CComSafeArray` .

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parámetros

*pBound*<br/>
Puntero a `SAFEARRAYBOUND` una estructura que contiene información sobre el número de elementos y el límite inferior de una matriz.

*ulCount*<br/>
El número solicitado de objetos en la matriz redimensionada.

*LLBound*<br/>
El límite inferior.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

Este método solo cambia el tamaño de la dimensión más a la derecha. No cambiará el tamaño `IsResizable` de las matrices que devuelven como FALSE.

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafeArray::SetAt

Establece el valor de un elemento de una matriz unidimensional.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parámetros

*Lindex*<br/>
El número de índice del elemento de matriz que se va a establecer.

*T*<br/>
Nuevo valor del elemento especificado.

*bCopy*<br/>
Indica si se debe crear una copia de los datos. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="remarks"></a>Observaciones

El indicador *bCopy* se tiene en cuenta cuando se agregan elementos de tipo BSTR o VARIANT a una matriz. El valor predeterminado de TRUE garantiza que se realiza una nueva copia de los datos cuando se agrega el elemento a la matriz.

## <a name="see-also"></a>Consulte también

[SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
