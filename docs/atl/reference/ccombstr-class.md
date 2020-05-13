---
title: Clase CComBSTR
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: c1448a5638b263a87403edf0baca170f0f952e26
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748138"
---
# <a name="ccombstr-class"></a>Clase CComBSTR

Esta clase es un contenedor para [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Sintaxis

```
class CComBSTR
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|El constructor.|
|[CComBSTR::-CComBSTR](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComBSTR::Append](#append)|Anexa una cadena `m_str`a .|
|[CComBSTR::AppendBSTR](#appendbstr)|Anexa un BSTR `m_str`a .|
|[CComBSTR::AppendBytes](#appendbytes)|Anexa un número especificado de `m_str`bytes a .|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crea un BSTR a partir del primer carácter de cada `CComBSTR` elemento de la safearray y lo adjunta al objeto.|
|[CComBSTR::AssignBSTR](#assignbstr)|Asigna un BSTR `m_str`a .|
|[CComBSTR::Attach](#attach)|Asocia un BSTR `CComBSTR` al objeto.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crea una matriz segura unidimensional basada en cero, donde cada `CComBSTR` elemento de la matriz es un carácter del objeto.|
|[CComBSTR::ByteLength](#bytelength)|Devuelve la `m_str` longitud de los bytes.|
|[CComBSTR::Copy](#copy)|Devuelve una `m_str`copia de .|
|[CComBSTR::CopyTo](#copyto)|Devuelve una `m_str` copia de via un parámetro **[out]**|
|[CComBSTR::Detach](#detach)|Se separa `m_str` `CComBSTR` del objeto.|
|[CComBSTR::Vacío](#empty)|Libera `m_str`.|
|[CComBSTR::Longitud](#length)|Devuelve la `m_str`longitud de .|
|[CComBSTR::LoadString](#loadstring)|Carga un recurso de cadena.|
|[CComBSTR::ReadFromStream](#readfromstream)|Carga un objeto BSTR desde una secuencia.|
|[CComBSTR::Tolower](#tolower)|Convierte la cadena en minúsculas.|
|[CComBSTR::ToUpper](#toupper)|Convierte la cadena en mayúsculas.|
|[CComBSTR::WriteTostream](#writetostream)|Guarda `m_str` en una secuencia.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComBSTR::operador BSTR](#operator_bstr)|Convierte un `CComBSTR` objeto en un BSTR.|
|[CComBSTR::operator !](#operator_not)|Devuelve TRUE o FALSE, `m_str`dependiendo de si es NULL.|
|[CComBSTR::operador !-](#operator_neq)|Compara a `CComBSTR` con una cadena.|
|[CComBSTR::operador &](#operator_amp)|Devuelve la `m_str`dirección de .|
|[CComBSTR::operador +o](#operator_add_eq)|Anexa `CComBSTR` a al objeto.|
|[CComBSTR::operador <](#operator_lt)|Compara a `CComBSTR` con una cadena.|
|[CComBSTR::operador ?](#operator_eq)|Asigna un valor `m_str`a .|
|[CComBSTR::operador ?](#operator_eq_eq)|Compara a `CComBSTR` con una cadena.|
|[CComBSTR::operador >](#operator_gt)|Compara a `CComBSTR` con una cadena.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Contiene el BSTR `CComBSTR` asociado al objeto.|

## <a name="remarks"></a>Observaciones

La `CComBSTR` clase es un contenedor para BSTRs, que son cadenas con prefijo de longitud. La longitud se almacena como un entero en la ubicación de memoria que precede a los datos de la cadena.

Un [BSTR](/previous-versions/windows/desktop/automat/bstr) es terminado en null después del último carácter contado, pero también puede contener caracteres nulos incrustados dentro de la cadena. La longitud de la cadena viene determinada por el recuento de caracteres, no por el primer carácter nulo.

> [!NOTE]
> La `CComBSTR` clase proporciona un número de miembros (constructores, operadores de asignación y operadores de comparación) que toman cadenas ANSI o Unicode como argumentos. Las versiones ANSI de estas funciones son menos eficaces que sus homólogos Unicode porque las cadenas Unicode temporales a menudo se crean internamente. Para mayor eficiencia, utilice las versiones Unicode siempre que sea posible.

> [!NOTE]
> Debido al comportamiento de búsqueda mejorado implementado en Visual `bstr = L"String2" + bstr;`Studio .NET, el código como , que `bstr = CStringW(L"String2") + bstr`puede haber compilado en versiones anteriores, en su lugar, debe implementarse como .

Para obtener una lista `CComBSTR`de precauciones al utilizar , consulte [Programación con CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR::Append

Anexa *lpsz* o el miembro BSTR de *bstrSrc* a [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[en] Objeto `CComBSTR` que se va a anexar.

*Ch*<br/>
[en] Un carácter para anexar.

*lpsz*<br/>
[en] Cadena de caracteres terminada en cero para anexar. Puede pasar una cadena Unicode a través de la sobrecarga LPCOLESTR o una cadena ANSI a través de la versión LPCSTR.

*nLen*<br/>
[en] El número de caracteres de *lpsz* para anexar.

### <a name="return-value"></a>Valor devuelto

S_OK en caso de éxito o de cualquier valor de error HRESULT estándar.

### <a name="remarks"></a>Observaciones

Una cadena ANSI se convertirá a Unicode antes de anexarse.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::AppendBSTR

Anexa el BSTR especificado a [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
[en] Un BSTR para anexar.

### <a name="return-value"></a>Valor devuelto

S_OK en caso de éxito o de cualquier valor de error HRESULT estándar.

### <a name="remarks"></a>Observaciones

No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::AppendBytes

Anexa el número especificado de bytes a [m_str](#m_str) sin conversión.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
[en] Puntero a una matriz de bytes para anexar.

*P*<br/>
[en] El número de bytes que se van a anexar.

### <a name="return-value"></a>Valor devuelto

S_OK en caso de éxito o de cualquier valor de error HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR

Libera cualquier cadena existente `CComBSTR` que se mantenga en el objeto y, a continuación, crea un BSTR a partir del primer carácter de cada elemento de la safearray y lo adjunta al `CComBSTR` objeto.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
[en] La barra fuerte que contiene los elementos utilizados para crear la cadena.

### <a name="return-value"></a>Valor devuelto

S_OK en caso de éxito o de cualquier valor de error HRESULT estándar.

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR

Asigna un BSTR a [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[en] Un BSTR para asignar `CComBSTR` al objeto actual.

### <a name="return-value"></a>Valor devuelto

S_OK en caso de éxito o de cualquier valor de error HRESULT estándar.

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR::Attach

Asocia un BSTR `CComBSTR` al objeto estableciendo el [m_str](#m_str) miembro *en src*.

```cpp
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] El BSTR que se va a adjuntar al objeto.

### <a name="remarks"></a>Observaciones

No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.

> [!NOTE]
> Este método afirmará si `m_str` no es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray

Crea una matriz segura unidimensional basada en cero, donde cada `CComBSTR` elemento de la matriz es un carácter del objeto.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
[fuera] Puntero a la barra fuerte utilizada para contener los resultados de la función.

### <a name="return-value"></a>Valor devuelto

S_OK en caso de éxito o de cualquier valor de error HRESULT estándar.

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::ByteLength

Devuelve el número `m_str`de bytes en , excluyendo el carácter nulo de terminación.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

La longitud del [miembro m_str](#m_str) en bytes.

### <a name="remarks"></a>Observaciones

Devuelve 0 `m_str` si es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR

El constructor. El constructor predeterminado establece el [m_str](#m_str) miembro en NULL.

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
[en] El número de caracteres que se van a `CComBSTR`copiar desde *sz* o el tamaño inicial en caracteres para el archivo .

*Sz*<br/>
[in] Cadena que se va a copiar. La versión Unicode especifica un LPCOLESTR; la versión ANSI especifica un LPCSTR.

*pSrc*<br/>
[in] Cadena que se va a copiar. La versión Unicode especifica un LPCOLESTR; la versión ANSI especifica un LPCSTR.

*src*<br/>
[in] Objeto `CComBSTR`.

*guid*<br/>
[en] Una referencia `GUID` a una estructura.

### <a name="remarks"></a>Observaciones

El constructor `m_str` de copia se establece en una copia del miembro BSTR de *src*. El `REFGUID` constructor convierte el GUID `StringFromGUID2` en una cadena mediante y almacena el resultado.

Los otros constructores establecen `m_str` en una copia de la cadena especificada. Si pasa un valor para *nSize*, solo se copiarán los caracteres *nSize,* seguidodes de un carácter nulo de terminación.

`CComBSTR` admite la semántica de transferencia de recursos. Puede usar el constructor de movimiento (el constructor que toma una referencia de valor R (`&&`) para crear un objeto nuevo que utiliza los mismos datos subyacentes que el objeto antiguo que se pasa como argumento, sin la sobrecarga a la hora de copiar el objeto.

El destructor libera la cadena a la que apunta `m_str`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR::-CComBSTR

Destructor.

```
~CComBSTR();
```

### <a name="remarks"></a>Observaciones

El destructor libera la cadena a la que apunta `m_str`.

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR::Copy

Asigna y devuelve una `m_str`copia de .

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Valor devuelto

Una copia del miembro [m_str.](#m_str) Si `m_str` es NULL, devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::CopyTo

Asigna y devuelve una copia de [m_str](#m_str) a través del parámetro.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parámetros

*pbstr*<br/>
[fuera] La dirección de un BSTR en el que se va a devolver la cadena asignada por este método.

*pvarDest*<br/>
[fuera] La dirección de un VARIANT en el que se va a devolver la cadena asignada por este método.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar que indica el éxito o el error de la copia.

### <a name="remarks"></a>Observaciones

Después de llamar a este método, el VARIANT señalado por *pvarDest* será de tipo VT_BSTR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach

Separa [m_str](#m_str) del `CComBSTR` objeto `m_str` y se establece en NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

El BSTR asociado `CComBSTR` al objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR::Vacío

Libera al miembro [de m_str.](#m_str)

```cpp
void Empty() throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR::Longitud

Devuelve el número `m_str`de caracteres de , excluyendo el carácter nulo de terminación.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Valor devuelto

La longitud del miembro [m_str.](#m_str)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::LoadString

Carga un recurso de cadena especificado por *nID* y lo almacena en este objeto.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parámetros

Consulte [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena se carga correctamente; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Observaciones

La primera función carga el recurso desde el módulo identificado por usted a través del parámetro *hInst.* La segunda función carga el recurso desde el módulo de recursos asociado con el [CComModule](../../atl/reference/ccommodule-class.md)-objeto derivado utilizado en este proyecto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR::m_str

Contiene el BSTR `CComBSTR` asociado al objeto.

```
BSTR m_str;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::operador BSTR

Convierte un `CComBSTR` objeto en un BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Observaciones

Le permite `CComBSTR` pasar objetos a funciones que tienen **parámetros BSTR [in].**

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComBSTR::m_str](#m_str).

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::operator !

Comprueba si la cadena BSTR es NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el [miembro m_str](#m_str) es NULL; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este operador solo comprueba si hay un valor NULL, no una cadena vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::operador !-

Devuelve el opuesto lógico del [operador](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[in] Objeto `CComBSTR`.

*pszSrc*<br/>
[en] Una cadena terminada en cero.

*nNull*<br/>
[en] Debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que `CComBSTR` se compara no es igual al objeto; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Observaciones

`CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. El operador de comparación final solo compara la cadena contenida con NULL.

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::operador&amp;

Devuelve la dirección del BSTR almacenado en el [miembro m_str.](#m_str)

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Observaciones

`CComBstr operator &`tiene una aserción especial asociada a ella para ayudar a identificar las fugas de memoria. El programa afirmará `m_str` cuando se inicialice el miembro. Esta aserción se creó para `& operator` identificar situaciones `m_str` en las que un `m_str`programador utiliza para asignar un nuevo valor al miembro sin liberar la primera asignación de . Si `m_str` es igual a NULL, el programa supone que aún no se ha asignado m_str. En este caso, el programa no afirmará.

Esta aserción no está habilitada de forma predeterminada. Defina ATL_CCOMBSTR_ADDRESS_OF_ASSERT para habilitar esta aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::operador +o

Anexa una cadena `CComBSTR` al objeto.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[en] Objeto `CComBSTR` que se va a anexar.

*pszSrc*<br/>
[en] Una cadena terminada en cero para anexar.

### <a name="remarks"></a>Observaciones

`CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. La comparación LPCOLESTR `memcmp` se realiza utilizando los datos sin procesar de cada cadena. La comparación LPCSTR se lleva a cabo de la misma manera una vez que se ha creado una copia Unicode temporal de *pszSrc.* El operador de comparación final solo compara la cadena contenida con NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::operador&lt;

Compara a `CComBSTR` con una cadena.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que `CComBSTR` se compara es menor que el objeto; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Observaciones

La comparación se realiza utilizando la configuración regional predeterminada del usuario.

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::operador ?

Establece el miembro [m_str](#m_str) en una copia de *pSrc* o en una copia del miembro BSTR de *src*. El operador de `src` asignación de movimiento se mueve sin copiarlo.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Observaciones

El parámetro *pSrc* especifica un LPCOLESTR para versiones Unicode o LPCSTR para versiones ANSI.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComBSTR::Copy](#copy).

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::operador ?

Compara a `CComBSTR` con una cadena. `CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[in] Objeto `CComBSTR`.

*pszSrc*<br/>
[en] Una cadena terminada en cero.

*nNull*<br/>
[en] Debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que `CComBSTR` se compara es igual al objeto; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Observaciones

El operador de comparación final solo compara la cadena contenida con NULL.

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::operador&gt;

Compara a `CComBSTR` con una cadena.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que `CComBSTR` se compara es mayor que el objeto; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Observaciones

La comparación se realiza utilizando la configuración regional predeterminada del usuario.

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::ReadFromStream

Establece el miembro [de m_str](#m_str) en el BSTR contenido en la secuencia especificada.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[en] Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en la secuencia que contiene los datos.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`ReadToStream`requiere que el contenido de la secuencia en la posición actual sea compatible con el formato de datos escrito por una llamada a [WriteToStream](#writetostream).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR::Tolower

Convierte la cadena contenida en minúsculas.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Consulte `CharLowerBuff` para obtener más información sobre cómo se realiza la conversión.

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::ToUpper

Convierte la cadena contenida en mayúsculas.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Consulte `CharUpperBuff` para obtener más información sobre cómo se realiza la conversión.

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteTostream

Guarda el miembro [m_str](#m_str) en una secuencia.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[en] Un puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en una secuencia.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Puede volver a crear un BSTR a partir del contenido de la secuencia mediante la función [ReadFromStream.](#readfromstream)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Macros de conversión de cadenas ATL y MFC](string-conversion-macros.md)
