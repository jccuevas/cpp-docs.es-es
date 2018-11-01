---
title: CComBSTR (clase)
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
ms.openlocfilehash: 52e8472e315932978af38d405c753b0a62fcbe45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475652"
---
# <a name="ccombstr-class"></a>CComBSTR (clase)

Esta clase es un contenedor para [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Sintaxis

```
class CComBSTR
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|El constructor.|
|[CComBSTR:: ~ CComBSTR](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComBSTR::Append](#append)|Anexa una cadena a `m_str`.|
|[CComBSTR::AppendBSTR](#appendbstr)|Anexa una cadena BSTR a `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Anexa un número especificado de bytes a `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crea una cadena BSTR desde el primer carácter de cada elemento de la matriz safearray y lo adjunta a la `CComBSTR` objeto.|
|[CComBSTR::AssignBSTR](#assignbstr)|Asigna un BSTR a `m_str`.|
|[CComBSTR::Attach](#attach)|Asocia un BSTR a la `CComBSTR` objeto.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crea un safearray unidimensional basado en cero, donde cada elemento de la matriz es un carácter de la `CComBSTR` objeto.|
|[CComBSTR::ByteLength](#bytelength)|Devuelve la longitud de `m_str` en bytes.|
|[CComBSTR::Copy](#copy)|Devuelve una copia de `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Devuelve una copia de `m_str` a través de un **[out]** parámetro|
|[CComBSTR::Detach](#detach)|Desasocia `m_str` desde el `CComBSTR` objeto.|
|[CComBSTR::Empty](#empty)|Libera `m_str`.|
|[CComBSTR::Length](#length)|Devuelve la longitud de `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Carga un recurso de cadena.|
|[CComBSTR::ReadFromStream](#readfromstream)|Carga un objeto BSTR desde una secuencia.|
|[CComBSTR::ToLower](#tolower)|Convierte la cadena a minúsculas.|
|[CComBSTR::ToUpper](#toupper)|Convierte la cadena a mayúsculas.|
|[CComBSTR::WriteToStream](#writetostream)|Guarda `m_str` en una secuencia.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CComBSTR::operator BSTR](#operator_bstr)|Convierte un `CComBSTR` objeto a un tipo BSTR.|
|[¡CComBSTR::operator!](#operator_not)|Devuelve TRUE o FALSE, dependiendo de si `m_str`es NULL.|
|[CComBSTR::operator! =](#operator_neq)|Compara un `CComBSTR` con una cadena.|
|[CComBSTR::operator &](#operator_amp)|Devuelve la dirección de `m_str`.|
|[CComBSTR::operator +=](#operator_add_eq)|Anexa un `CComBSTR` al objeto.|
|[CComBSTR::operator <](#operator_lt)|Compara un `CComBSTR` con una cadena.|
|[CComBSTR::operator =](#operator_eq)|Asigna un valor a `m_str`.|
|[CComBSTR::operator ==](#operator_eq_eq)|Compara un `CComBSTR` con una cadena.|
|[CComBSTR::operator >](#operator_gt)|Compara un `CComBSTR` con una cadena.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Contiene el BSTR asociado con el `CComBSTR` objeto.|

## <a name="remarks"></a>Comentarios

La `CComBSTR` clase es un contenedor de cadenas BSTR, que son cadenas de longitud fija. La longitud se almacena como un entero en la ubicación de memoria antes de los datos en la cadena.

Un [BSTR](/previous-versions/windows/desktop/automat/bstr) está terminada en null después de la última cuenta carácter pero también puede contener caracteres nulos incrustados dentro de la cadena. La longitud de cadena viene determinada por el recuento de caracteres, no el primer carácter nulo.

> [!NOTE]
>  La `CComBSTR` clase proporciona un número de miembros (constructores, operadores de asignación y operadores de comparación) que toman cadenas ANSI o Unicode como argumentos. Las versiones ANSI de estas funciones son menos eficientes que sus equivalentes Unicode como cadenas Unicode temporales a menudo se crean internamente. Para mejorar la eficacia, use las versiones Unicode siempre que sea posible.

> [!NOTE]
>  Debido al comportamiento de búsqueda mejorada implementado en Visual Studio. NET, un código como `bstr = L"String2" + bstr;`, que es posible que haya compilado en versiones anteriores, en su lugar, debe implementarse como `bstr = CStringW(L"String2") + bstr`.

Para obtener una lista de precauciones al usar `CComBSTR`, consulte [programar con CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="append"></a>  CComBSTR::Append

Anexa una *lpsz* o el miembro BSTR de *bstrSrc* a [m_str](#m_str).

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
[in] Un `CComBSTR` objeto que se va a anexar.

*CH*<br/>
[in] Un carácter que se va a anexar.

*lpsz*<br/>
[in] Una cadena de caracteres terminada en cero para anexar. Puede pasar una cadena Unicode a través de la sobrecarga LPCOLESTR o una cadena ANSI a través de la versión LPCSTR.

*nLen*<br/>
[in] El número de caracteres de *lpsz* para anexar.

### <a name="return-value"></a>Valor devuelto

S_OK si funciona correctamente, o cualquier valor de error HRESULT estándar.

### <a name="remarks"></a>Comentarios

Una cadena ANSI se convertirá a Unicode antes de que se va a anexar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

Anexa el BSTR especificado a [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
[in] Para anexar un BSTR.

### <a name="return-value"></a>Valor devuelto

S_OK si funciona correctamente, o cualquier valor de error HRESULT estándar.

### <a name="remarks"></a>Comentarios

No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>  CComBSTR::AppendBytes

Anexa el número especificado de bytes a [m_str](#m_str) sin conversión.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
[in] Un puntero a una matriz de bytes que se anexará.

*p*<br/>
[in] El número de bytes que se anexará.

### <a name="return-value"></a>Valor devuelto

S_OK si funciona correctamente, o cualquier valor de error HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

Libera cualquier cadena existente que se mantienen en el `CComBSTR` objeto, a continuación, crea una cadena BSTR desde el primer carácter de cada elemento de la matriz safearray y lo adjunta a la `CComBSTR` objeto.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
[in] Safearray que contiene los elementos utilizados para crear la cadena.

### <a name="return-value"></a>Valor devuelto

S_OK si funciona correctamente, o cualquier valor de error HRESULT estándar.

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

Asigna un BSTR a [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[in] Una cadena BSTR para asignar a la actual `CComBSTR` objeto.

### <a name="return-value"></a>Valor devuelto

S_OK si funciona correctamente, o cualquier valor de error HRESULT estándar.

##  <a name="attach"></a>  CComBSTR::Attach

Asocia un BSTR a la `CComBSTR` objeto estableciendo la [m_str](#m_str) miembro *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] BSTR que se va a adjuntar al objeto.

### <a name="remarks"></a>Comentarios

No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.

> [!NOTE]
>  Este método se producirá una aserción si `m_str` es distinto de NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>  CComBSTR::BSTRToArray

Crea un safearray unidimensional basado en cero, donde cada elemento de la matriz es un carácter de la `CComBSTR` objeto.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
[out] Puntero a la matriz safearray utilizado para almacenar los resultados de la función.

### <a name="return-value"></a>Valor devuelto

S_OK si funciona correctamente, o cualquier valor de error HRESULT estándar.

##  <a name="bytelength"></a>  CComBSTR::ByteLength

Devuelve el número de bytes en `m_str`, excluido el carácter nulo de terminación.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

La longitud de la [m_str](#m_str) miembro en bytes.

### <a name="remarks"></a>Comentarios

Devuelve 0 si `m_str` es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>  CComBSTR::CComBSTR

El constructor. El constructor predeterminado establece la [m_str](#m_str) miembro en NULL.

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

*nSize*<br/>
[in] El número de caracteres que se va a copiar de *sz* o el tamaño inicial en caracteres para el `CComBSTR`.

*sz*<br/>
[in] Cadena que se va a copiar. La versión Unicode especifica un LPCOLESTR; la versión ANSI especifica un LPCSTR.

*pSrc*<br/>
[in] Cadena que se va a copiar. La versión Unicode especifica un LPCOLESTR; la versión ANSI especifica un LPCSTR.

*src*<br/>
[in] Objeto `CComBSTR`.

*GUID*<br/>
[in] Una referencia a un `GUID` estructura.

### <a name="remarks"></a>Comentarios

El constructor de copia establece `m_str` a una copia del miembro de BSTR *src*. El `REFGUID` constructor convierte el GUID en una cadena mediante `StringFromGUID2` y almacena el resultado.

Los otros constructores establecen `m_str` en una copia de la cadena especificada. Si se pasa un valor para *nSize*, solo *nSize* se copiará caracteres, seguido por un carácter nulo de terminación.

`CComBSTR` admite la semántica de transferencia de recursos. Puede usar el constructor de movimiento (el constructor que toma una referencia de valor R (`&&`) para crear un objeto nuevo que utiliza los mismos datos subyacentes que el objeto antiguo que se pasa como argumento, sin la sobrecarga a la hora de copiar el objeto.

El destructor libera la cadena a la que apunta `m_str`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>  CComBSTR:: ~ CComBSTR

Destructor.

```
~CComBSTR();
```

### <a name="remarks"></a>Comentarios

El destructor libera la cadena a la que apunta `m_str`.

##  <a name="copy"></a>  CComBSTR::Copy

Asigna y devuelve una copia de `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Valor devuelto

Una copia de la [m_str](#m_str) miembro. Si `m_str` es NULL, devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>  CComBSTR::CopyTo

Asigna y devuelve una copia de [m_str](#m_str) a través del parámetro.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parámetros

*pbstr*<br/>
[out] La dirección del BSTR en la que se va a devolver la cadena asignada por este método.

*pvarDest*<br/>
[out] La dirección de una variante en el que se va a devolver la cadena asignada por este método.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar que indica el éxito o fracaso de la copia.

### <a name="remarks"></a>Comentarios

Después de llamar a este método, la variante apunta *pvarDest* será de tipo VT_BSTR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

Desasocia [m_str](#m_str) desde el `CComBSTR` objeto y establece `m_str` en NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

El BSTR asociado con el `CComBSTR` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>  CComBSTR::Empty

Libera el [m_str](#m_str) miembro.

```
void Empty() throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>  CComBSTR::Length

Devuelve el número de caracteres en `m_str`, excluido el carácter nulo de terminación.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Valor devuelto

La longitud de la [m_str](#m_str) miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

Carga un recurso de cadena especificado por *nID* y lo almacena en este objeto.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parámetros

Consulte [LoadString](/windows/desktop/api/winuser/nf-winuser-loadstringa) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena se carga correctamente; en caso contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

La primera función carga el recurso desde el módulo identificado por el usuario a través de la *hInst* parámetro. La segunda función carga el recurso desde el módulo de recursos asociado con el [CComModule](../../atl/reference/ccommodule-class.md)-derivados de objeto que se usa en este proyecto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

Contiene el BSTR asociado con el `CComBSTR` objeto.

```
BSTR m_str;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>  CComBSTR::operator BSTR

Convierte un `CComBSTR` objeto a un tipo BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Comentarios

Le permite pasar `CComBSTR` objetos a funciones que tienen **[in] BSTR** parámetros.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComBSTR::m_str](#m_str).

##  <a name="operator_not"></a>  ¡CComBSTR::operator!

Comprueba si la cadena BSTR es NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el [m_str](#m_str) miembro es NULL; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este operador solo busca un valor NULL, no para una cadena vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>  CComBSTR::operator! =

Devuelve el lógico opuesto [operador ==](#operator_eq_eq).

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
[in] Una cadena terminada en cero.

*nNull*<br/>
[in] Debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que se compara no es igual a la `CComBSTR` objeto; en caso contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

`CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. El operador de comparación final sencillamente compara la cadena contenida con valores NULL.

##  <a name="operator_amp"></a>  CComBSTR::operator &amp;

Devuelve la dirección del BSTR que se almacenan en el [m_str](#m_str) miembro.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Comentarios

`CComBstr operator &` tiene una aserción especial asociados con él para ayudar a identificar pérdidas de memoria. El programa producirá una aserción cuando el `m_str` se puede inicializar el miembro. Esta aserción se creó para identificar las situaciones donde un programador utiliza el `& operator` para asignar un nuevo valor a `m_str` miembro sin liberar la primera asignación de `m_str`. Si `m_str` es igual a NULL, el programa se da por supuesto que m_str no se ha asignado todavía. En este caso, el programa no se producirá una aserción.

Esta aserción no está habilitada de forma predeterminada. Definir ATL_CCOMBSTR_ADDRESS_OF_ASSERT para habilitar esta aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>  CComBSTR::operator +=

Anexa una cadena a la `CComBSTR` objeto.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
[in] Un `CComBSTR` objeto que se va a anexar.

*pszSrc*<br/>
[in] Una cadena terminada en cero para anexar.

### <a name="remarks"></a>Comentarios

`CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. Se realiza la comparación LPCOLESTR mediante `memcmp` en los datos sin procesar en cada cadena. La comparación LPCSTR se realiza en la misma manera cuando copie Unicode temporal de *pszSrc* se ha creado. El operador de comparación final sencillamente compara la cadena contenida con valores NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>  CComBSTR::operator &lt;

Compara un `CComBSTR` con una cadena.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que se compara es menor que el `CComBSTR` objeto; en caso contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

La comparación se realiza mediante la configuración regional predeterminada del usuario.

##  <a name="operator_eq"></a>  CComBSTR::operator =

Establece el [m_str](#m_str) miembro a una copia de *pSrc* o a una copia del miembro de BSTR *src*. Mueve el operador de asignación de movimiento `src` sin copiarlo.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Comentarios

El *pSrc* parámetro especifica un LPCOLESTR para las versiones de Unicode o LPCSTR para versiones ANSI.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComBSTR::Copy](#copy).

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

Compara un `CComBSTR` con una cadena. `CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario.

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
[in] Una cadena terminada en cero.

*nNull*<br/>
[in] Debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que se compara es igual a la `CComBSTR` objeto; en caso contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

El operador de comparación final sencillamente compara la cadena contenida con valores NULL.

##  <a name="operator_gt"></a>  CComBSTR::operator &gt;

Compara un `CComBSTR` con una cadena.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que se compara es mayor que el `CComBSTR` objeto; en caso contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

La comparación se realiza mediante la configuración regional predeterminada del usuario.

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

Establece el [m_str](#m_str) miembro para el BSTR contenido en la secuencia especificada.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[in] Un puntero a la [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfaz en la secuencia que contiene los datos.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`ReadToStream` requiere el contenido de la secuencia en la posición actual para que sea compatible con el formato de datos escrito por una llamada a [WriteToStream](#writetostream).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

Convierte la cadena contenida en minúsculas.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Consulte `CharLowerBuff` para obtener más información sobre cómo se realiza la conversión.

##  <a name="toupper"></a>  CComBSTR::ToUpper

Convierte la cadena contenida en mayúsculas.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Consulte `CharUpperBuff` para obtener más información sobre cómo se realiza la conversión.

##  <a name="writetostream"></a>  CComBSTR::WriteToStream

Guarda el [m_str](#m_str) miembro en una secuencia.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
[in] Un puntero a la [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfaz en una secuencia.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Puede volver a crear una cadena BSTR del contenido de la secuencia utilizando el [ReadFromStream](#readfromstream) función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Macros de conversión de cadena MFC y ATL](string-conversion-macros.md)
