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
ms.openlocfilehash: 79b1dc844f53f739dc48eb6177e57810ff0c8412
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739589"
---
# <a name="ccomsafearray-class"></a>CComSafeArray (clase)

Esta clase es un contenedor para la `SAFEARRAY` estructura.

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

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|El constructor.|
|[CComSafeArray::~CComSafeArray](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComSafeArray::Add](#add)|Agrega uno o más elementos, o una `SAFEARRAY` estructura, a un `CComSafeArray`.|
|[CComSafeArray::Attach](#attach)|Asocia una `SAFEARRAY` estructura a un `CComSafeArray` objeto.|
|[CComSafeArray::CopyFrom](#copyfrom)|Copia el contenido de una `SAFEARRAY` estructura en el `CComSafeArray` objeto.|
|[CComSafeArray::CopyTo](#copyto)|Crea una copia del objeto `CComSafeArray` .|
|[CComSafeArray::Create](#create)|Crea un objeto `CComSafeArray`.|
|[CComSafeArray::Destroy](#destroy)|Destruye un objeto `CComSafeArray`.|
|[CComSafeArray::Detach](#detach)|Desasocia un `SAFEARRAY` de un `CComSafeArray` objeto.|
|[CComSafeArray::GetAt](#getat)|Recupera un único elemento de una matriz unidimensional.|
|[CComSafeArray::GetCount](#getcount)|Devuelve el número de elementos de la matriz.|
|[CComSafeArray::GetDimensions](#getdimensions)|Devuelve el número de dimensiones de la matriz.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Devuelve el límite inferior de una determinada dimensión de la matriz.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Devuelve la dirección del miembro de datos `m_psa` .|
|[CComSafeArray::GetType](#gettype)|Devuelve el tipo de datos almacenado en la matriz.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Devuelve el límite superior de cualquier dimensión de la matriz.|
|[CComSafeArray::IsSizable](#issizable)|Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Recupera un único elemento de una matriz multidimensional.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Establece el valor de un elemento de una matriz multidimensional.|
|[CComSafeArray::Resize](#resize)|Cambia el tamaño de un objeto `CComSafeArray` .|
|[CComSafeArray::SetAt](#setat)|Establece el valor de un elemento de una matriz unidimensional.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComSafeArray:: Operator LPSAFEARRAY](#operator_lpsafearray)|Convierte un valor en un `SAFEARRAY` puntero.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Recupera un elemento de la matriz.|
|[CComSafeArray::operator =](#operator_eq)|Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Este miembro de datos contiene la dirección de `SAFEARRAY` la estructura.|

## <a name="remarks"></a>Comentarios

`CComSafeArray` proporciona un contenedor para la clase [SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray) , lo que facilita la creación y administración de matrices unidimensionales y multidimensionales de casi cualquiera de los tipos compatibles VARIANT.

`CComSafeArray` simplifica el paso de matrices entre procesos y, además, proporciona seguridad adicional al comprobar los valores de índice de matriz con los limites superior e inferior.

El límite inferior de `CComSafeArray` puede empezar por cualquier valor definido por el usuario, pero las matrices a las que se accede a través de C++ usan un límite inferior de 0. Otros lenguajes como Visual Basic pueden usar otros valores límite (por ejemplo, de -10 a 10).

Use [CComSafeArray::Create](#create) para crear un objeto `CComSafeArray` y [CComSafeArray::Destroy](#destroy) para eliminarlo.

Un elemento `CComSafeArray` puede contener el siguiente subconjunto de tipos de datos VARIANT:

|VARTYPE|DESCRIPCIÓN|
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
|VT_R4|float|
|VT_R8|Doble|
|VT_DECIMAL|puntero decimal|
|VT_VARIANT|puntero variant|
|VT_CY|Currency (tipo de datos)|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsafe.h

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>  CComSafeArray::Add

Agrega uno o más elementos, o una `SAFEARRAY` estructura, a un `CComSafeArray`.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parámetros

*psaSrc*<br/>
Puntero a un objeto `SAFEARRAY` .

*ulCount*<br/>
Número de objetos que se van a agregar a la matriz.

*pT*<br/>
Puntero a uno o varios objetos que se van a agregar a la matriz.

*t*<br/>
Referencia al objeto que se va a agregar a la matriz.

*bCopy*<br/>
Indica si se debe crear una copia de los datos. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Los objetos nuevos se anexan al final del objeto existente `SAFEARRAY` . No se admite la adición de un objeto `SAFEARRAY` a un objeto multidimensional. Al agregar una matriz de objetos existente, ambas matrices deben contener elementos del mismo tipo.

La marca *bCopy* se tiene en cuenta cuando se agregan elementos de tipo BSTR o Variant a una matriz. El valor predeterminado TRUE garantiza que se crea una nueva copia de los datos cuando el elemento se agrega a la matriz.

##  <a name="attach"></a>  CComSafeArray::Attach

Asocia una `SAFEARRAY` estructura a un `CComSafeArray` objeto.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parámetros

*psaSrc*<br/>
Puntero a la `SAFEARRAY` estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Asocia una `SAFEARRAY` estructura a un `CComSafeArray` objeto, haciendo que los métodos `CComSafeArray` existentes estén disponibles.

##  <a name="ccomsafearray"></a>  CComSafeArray::CComSafeArray

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

*enlaza*<br/>
Un estructura `SAFEARRAYBOUND`.

*ulCount*<br/>
Número de elementos de la matriz.

*lLBound*<br/>
Valor de límite inferior; es decir, el índice del primer elemento de la matriz.

*pBound*<br/>
Puntero a una `SAFEARRAYBOUND` estructura.

*uDims*<br/>
Número de dimensiones de la matriz.

*saSrc*<br/>
Referencia a una `SAFEARRAY` estructura u `CComSafeArray` objeto. En cualquier caso, el constructor utiliza esta referencia para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.

*psaSrc*<br/>
Puntero a una `SAFEARRAY` estructura. El constructor utiliza esta dirección para hacer una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.

### <a name="remarks"></a>Comentarios

Crea un objeto `CComSafeArray`.

##  <a name="dtor"></a>  CComSafeArray::~CComSafeArray

Destructor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="copyfrom"></a>  CComSafeArray::CopyFrom

Copia el contenido de una `SAFEARRAY` estructura en el `CComSafeArray` objeto.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
Puntero al `SAFEARRAY` que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este método copia el contenido de `SAFEARRAY` en el objeto actual. `CComSafeArray` Se reemplaza el contenido existente de la matriz.

##  <a name="copyto"></a>  CComSafeArray::CopyTo

Crea una copia del objeto `CComSafeArray` .

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
Puntero a una ubicación en la que se va a crear `SAFEARRAY`el nuevo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este método copia el contenido de un `CComSafeArray` objeto en una `SAFEARRAY` estructura.

##  <a name="create"></a>  CComSafeArray::Create

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

*lLBound*<br/>
Valor de límite inferior; es decir, el índice del primer elemento de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Un `CComSafeArray` objeto se puede crear a partir de `SAFEARRAYBOUND` una estructura existente y el número de dimensiones, o especificando el número de elementos de la matriz y el límite inferior. Si se va a tener acceso a la matriz C++desde, el límite inferior debe ser 0. Otros lenguajes pueden permitir otros valores para el límite inferior (por ejemplo, Visual Basic admite matrices con elementos con un intervalo como-10 a 10).

##  <a name="destroy"></a>  CComSafeArray::Destroy

Destruye un objeto `CComSafeArray`.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Destruye un objeto existente `CComSafeArray` y todos los datos que contiene.

##  <a name="detach"></a>  CComSafeArray::Detach

Desasocia un `SAFEARRAY` de un `CComSafeArray` objeto.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a un `SAFEARRAY` objeto.

### <a name="remarks"></a>Comentarios

Este método Desasocia el `SAFEARRAY` objeto `CComSafeArray` del objeto.

##  <a name="getat"></a>  CComSafeArray::GetAt

Recupera un único elemento de una matriz unidimensional.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parámetros

*lIndex*<br/>
Número de índice del valor de la matriz que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia al elemento de matriz necesario.

##  <a name="getcount"></a>  CComSafeArray::GetCount

Devuelve el número de elementos de la matriz.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parámetros

*uDim*<br/>
La dimensión de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos de la matriz.

### <a name="remarks"></a>Comentarios

Cuando se usa con una matriz multidimensional, este método devolverá solo el número de elementos de una dimensión específica.

##  <a name="getdimensions"></a>  CComSafeArray::GetDimensions

Devuelve el número de dimensiones de la matriz.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de dimensiones de la matriz.

##  <a name="getlowerbound"></a>  CComSafeArray::GetLowerBound

Devuelve el límite inferior de una determinada dimensión de la matriz.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parámetros

*uDim*<br/>
La dimensión de la matriz para la que se va a obtener el límite inferior. Si se omite, el valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

Devuelve el límite inferior.

### <a name="remarks"></a>Comentarios

Si el límite inferior es 0, indica una matriz similar a C cuyo primer elemento es el número de elemento 0. En caso de error, por ejemplo, un argumento de dimensión no válido, este método llama `AtlThrow` a con un valor HRESULT que describe el error.

##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr

Devuelve la dirección del miembro de datos `m_psa` .

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al miembro de datos [CComSafeArray:: m_psa](#m_psa) .

##  <a name="gettype"></a>  CComSafeArray::GetType

Devuelve el tipo de datos almacenado en la matriz.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el tipo de datos almacenado en la matriz, que puede ser cualquiera de los siguientes tipos:

|VARTYPE|DESCRIPCIÓN|
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
|VT_R4|float|
|VT_R8|Doble|
|VT_DECIMAL|puntero decimal|
|VT_VARIANT|puntero variant|
|VT_CY|Currency (tipo de datos)|

##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound

Devuelve el límite superior de cualquier dimensión de la matriz.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parámetros

*uDim*<br/>
La dimensión de la matriz para la que se va a obtener el límite superior. Si se omite, el valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

Devuelve el límite superior. Este valor es inclusivo, el índice válido máximo para esta dimensión.

### <a name="remarks"></a>Comentarios

En caso de error, por ejemplo, un argumento de dimensión no válido, este método llama `AtlThrow` a con un valor HRESULT que describe el error.

##  <a name="issizable"></a>  CComSafeArray::IsSizable

Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .

```
bool IsSizable() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si se `CComSafeArray` puede cambiar el tamaño de, false si no puede.

##  <a name="m_psa"></a>  CComSafeArray::m_psa

Contiene la dirección de la `SAFEARRAY` estructura a la que se obtiene acceso.

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>  CComSafeArray::MultiDimGetAt

Recupera un único elemento de una matriz multidimensional.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parámetros

*alIndex*<br/>
Puntero a un vector de índices para cada dimensión de la matriz. La dimensión situada más a la izquierda ( `alIndex[0]`más importante) es.

*t*<br/>
Referencia a los datos devueltos.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt

Establece el valor de un elemento de una matriz multidimensional.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parámetros

*alIndex*<br/>
Puntero a un vector de índices para cada dimensión de la matriz. La dimensión situada más a la derecha ( `alIndex`menos significativa) es [0].

*T*<br/>
Especifica el valor del nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Se trata de una versión multidimensional de [CComSafeArray:: SetAt](#setat).

##  <a name="operator_at"></a>CComSafeArray:: Operator\[\]

Recupera un elemento de la matriz.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parámetros

*lIndex, nIndex*<br/>
Número de índice del elemento necesario de la matriz.

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento de matriz adecuado.

### <a name="remarks"></a>Comentarios

Realiza una función similar a [CComSafeArray:: getadt](#getat); sin embargo, este operador solo funciona con matrices unidimensionales.

##  <a name="operator_eq"></a>CComSafeArray:: Operator =

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

##  <a name="operator_lpsafearray"></a>CComSafeArray:: Operator LPSAFEARRAY

Convierte un valor en un `SAFEARRAY` puntero.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Valor devuelto

Convierte un valor en un `SAFEARRAY` puntero.

##  <a name="resize"></a>  CComSafeArray::Resize

Cambia el tamaño de un objeto `CComSafeArray` .

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parámetros

*pBound*<br/>
Puntero a una `SAFEARRAYBOUND` estructura que contiene información sobre el número de elementos y el límite inferior de una matriz.

*ulCount*<br/>
Número solicitado de objetos en la matriz cuyo tamaño se ha cambiado.

*lLBound*<br/>
Límite inferior.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

Este método solo cambia el tamaño de la dimensión situada más a la derecha. No cambiará el tamaño de las matrices que `IsResizable` devuelven como false.

##  <a name="setat"></a>  CComSafeArray::SetAt

Establece el valor de un elemento de una matriz unidimensional.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parámetros

*lIndex*<br/>
Número de índice del elemento de la matriz que se va a establecer.

*t*<br/>
Nuevo valor del elemento especificado.

*bCopy*<br/>
Indica si se debe crear una copia de los datos. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="remarks"></a>Comentarios

La marca *bCopy* se tiene en cuenta cuando se agregan elementos de tipo BSTR o Variant a una matriz. El valor predeterminado TRUE garantiza que se crea una nueva copia de los datos cuando el elemento se agrega a la matriz.

## <a name="see-also"></a>Vea también

[SAFEARRAY, tipo de datos](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
