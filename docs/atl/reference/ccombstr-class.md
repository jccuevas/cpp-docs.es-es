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
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497552"
---
# <a name="ccombstr-class"></a>CComBSTR (clase)

Esta clase es un contenedor para [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Sintaxis

```
class CComBSTR
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|El constructor.|
|[CComBSTR::~CComBSTR](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComBSTR::Append](#append)|Anexa una cadena a `m_str`.|
|[CComBSTR::AppendBSTR](#appendbstr)|Anexa un BSTR a `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Anexa un número especificado de bytes a `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crea un BSTR a partir del primer carácter de cada elemento de la matriz SafeArray y lo adjunta al `CComBSTR` objeto.|
|[CComBSTR::AssignBSTR](#assignbstr)|Asigna un BSTR a `m_str`.|
|[CComBSTR::Attach](#attach)|Adjunta un BSTR al `CComBSTR` objeto.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crea un SafeArray unidimensional de base cero, donde cada elemento de la matriz es un carácter del `CComBSTR` objeto.|
|[CComBSTR::ByteLength](#bytelength)|Devuelve la longitud de `m_str` en bytes.|
|[CComBSTR::Copy](#copy)|Devuelve una copia de `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Devuelve una copia de `m_str` a través de un parámetro **[out]** .|
|[CComBSTR::Detach](#detach)|Desasocia `m_str` del objeto `CComBSTR` .|
|[CComBSTR::Empty](#empty)|`m_str`Libera.|
|[CComBSTR::Length](#length)|Devuelve la longitud de `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Carga un recurso de cadena.|
|[CComBSTR::ReadFromStream](#readfromstream)|Carga un objeto BSTR desde una secuencia.|
|[CComBSTR::ToLower](#tolower)|Convierte la cadena a minúsculas.|
|[CComBSTR::ToUpper](#toupper)|Convierte la cadena en mayúsculas.|
|[CComBSTR::WriteToStream](#writetostream)|Guarda `m_str` en un flujo.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComBSTR:: Operator BSTR](#operator_bstr)|Convierte un `CComBSTR` objeto en un BSTR.|
|[CComBSTR:: Operator!](#operator_not)|Devuelve true o false, dependiendo de si `m_str`es NULL.|
|[CComBSTR::operator !=](#operator_neq)|`CComBSTR` Compara con una cadena.|
|[CComBSTR::operator &](#operator_amp)|Devuelve la dirección de `m_str`.|
|[CComBSTR::operator +=](#operator_add_eq)|`CComBSTR` Anexa al objeto.|
|[CComBSTR:: Operator <](#operator_lt)|`CComBSTR` Compara con una cadena.|
|[CComBSTR::operator =](#operator_eq)|Asigna un valor a `m_str`.|
|[CComBSTR::operator ==](#operator_eq_eq)|`CComBSTR` Compara con una cadena.|
|[CComBSTR::operator >](#operator_gt)|`CComBSTR` Compara con una cadena.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Contiene el BSTR asociado al `CComBSTR` objeto.|

## <a name="remarks"></a>Comentarios

La `CComBSTR` clase es un contenedor para BSTR, que son cadenas con prefijo de longitud. La longitud se almacena como un entero en la ubicación de memoria que precede a los datos de la cadena.

Un [BSTR](/previous-versions/windows/desktop/automat/bstr) termina en NULL después del último carácter contado, pero también puede contener caracteres null incrustados dentro de la cadena. La longitud de la cadena viene determinada por el recuento de caracteres, no por el primer carácter nulo.

> [!NOTE]
>  La `CComBSTR` clase proporciona una serie de miembros (constructores, operadores de asignación y operadores de comparación) que aceptan cadenas ANSI o Unicode como argumentos. Las versiones ANSI de estas funciones son menos eficientes que sus homólogos Unicode, ya que las cadenas Unicode temporales suelen crearse internamente. Por motivos de eficacia, use las versiones Unicode siempre que sea posible.

> [!NOTE]
>  Debido al mejor comportamiento de búsqueda implementado en Visual Studio .net, el código `bstr = L"String2" + bstr;`como, que puede haberse compilado en versiones anteriores, en su lugar se debe `bstr = CStringW(L"String2") + bstr`implementar como.

Para obtener una lista de precauciones al usar `CComBSTR`, vea [programar con CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="append"></a>  CComBSTR::Append

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
de `CComBSTR` Objeto que se va a anexar.

*ch*<br/>
de Carácter que se va a anexar.

*lpsz*<br/>
de Cadena de caracteres terminada en cero que se va a anexar. Puede pasar una cadena Unicode a través de la sobrecarga LPCOLESTR o una cadena ANSI a través de la versión de LPCSTR.

*nLen*<br/>
de Número de caracteres de *lpsz* que se van a anexar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente o cualquier valor de error HRESULT estándar.

### <a name="remarks"></a>Comentarios

Una cadena ANSI se convertirá a Unicode antes de anexarse.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

Anexa el BSTR especificado a [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
de BSTR que se va a anexar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente o cualquier valor de error HRESULT estándar.

### <a name="remarks"></a>Comentarios

No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores en tiempo de ejecución.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>  CComBSTR::AppendBytes

Anexa el número especificado de bytes a [m_str](#m_str) sin conversión.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parámetros

*lpsz*<br/>
de Puntero a una matriz de bytes que se va a anexar.

*p*<br/>
de Número de bytes que se van a anexar.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente o cualquier valor de error HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

Libera cualquier cadena existente almacenada en el `CComBSTR` objeto y, a continuación, crea un BSTR a partir del primer carácter de cada elemento de la matriz SafeArray y `CComBSTR` lo adjunta al objeto.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parámetros

*pSrc*<br/>
de SafeArray que contiene los elementos usados para crear la cadena.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente o cualquier valor de error HRESULT estándar.

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

Asigna un BSTR a [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
de BSTR que se va a asignar al `CComBSTR` objeto actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente o cualquier valor de error HRESULT estándar.

##  <a name="attach"></a>  CComBSTR::Attach

Adjunta un BSTR al `CComBSTR` objeto estableciendo el miembro [m_str](#m_str) en *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parámetros

*src*<br/>
de BSTR que se va a adjuntar al objeto.

### <a name="remarks"></a>Comentarios

No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores en tiempo de ejecución.

> [!NOTE]
>  Este método validará si `m_str` no es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>  CComBSTR::BSTRToArray

Crea un SafeArray unidimensional de base cero, donde cada elemento de la matriz es un carácter del `CComBSTR` objeto.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parámetros

*ppArray*<br/>
enuncia Puntero al SafeArray que se usa para contener los resultados de la función.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente o cualquier valor de error HRESULT estándar.

##  <a name="bytelength"></a>  CComBSTR::ByteLength

Devuelve el número de bytes de `m_str`, sin incluir el carácter nulo de terminación.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

La longitud del miembro [m_str](#m_str) en bytes.

### <a name="remarks"></a>Comentarios

Devuelve 0 si `m_str` es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>  CComBSTR::CComBSTR

El constructor. El constructor predeterminado establece el miembro [m_str](#m_str) en NULL.

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
de Número de caracteres que se van a copiar desde *SZ* o el tamaño inicial en caracteres `CComBSTR`para.

*sz*<br/>
[in] Cadena que se va a copiar. La versión Unicode especifica un LPCOLESTR; la versión ANSI especifica un LPCSTR.

*pSrc*<br/>
[in] Cadena que se va a copiar. La versión Unicode especifica un LPCOLESTR; la versión ANSI especifica un LPCSTR.

*src*<br/>
[in] Objeto `CComBSTR`.

*guid*<br/>
de Referencia a una `GUID` estructura.

### <a name="remarks"></a>Comentarios

El constructor de copias `m_str` establece en una copia del miembro BSTR de *src*. El `REFGUID` constructor convierte el GUID en una cadena mediante `StringFromGUID2` y almacena el resultado.

Los otros constructores establecen `m_str` en una copia de la cadena especificada. Si pasa un valor para *nSize*, solo se copiarán los caracteres *nSize* , seguidos de un carácter nulo de terminación.

`CComBSTR` admite la semántica de transferencia de recursos. Puede usar el constructor de movimiento (el constructor que toma una referencia de valor R (`&&`) para crear un objeto nuevo que utiliza los mismos datos subyacentes que el objeto antiguo que se pasa como argumento, sin la sobrecarga a la hora de copiar el objeto.

El destructor libera la cadena a la que apunta `m_str`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>  CComBSTR::~CComBSTR

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

Una copia del miembro [m_str](#m_str) . Si `m_str` es null, devuelve NULL.

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
enuncia Dirección de un BSTR en el que se va a devolver la cadena asignada por este método.

*pvarDest*<br/>
enuncia Dirección de una variante en la que se va a devolver la cadena asignada por este método.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar que indica si la copia se ha realizado correctamente o no.

### <a name="remarks"></a>Comentarios

Después de llamar a este método, la variante a la que señala *pvarDest* será de tipo VT_BSTR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

Desasocia [m_str](#m_str) del `CComBSTR` objeto y establece `m_str` en NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

BSTR asociado al `CComBSTR` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>  CComBSTR::Empty

Libera el miembro [m_str](#m_str) .

```
void Empty() throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>  CComBSTR::Length

Devuelve el número de caracteres de `m_str`, sin incluir el carácter nulo de terminación.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Valor devuelto

La longitud del miembro [m_str](#m_str) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

Carga un recurso de cadena especificado por *nID* y lo almacena en este objeto.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parámetros

Vea [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la cadena se ha cargado correctamente; de lo contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

La primera función carga el recurso desde el módulo identificado mediante el parámetro *HINST* . La segunda función carga el recurso del módulo de recursos asociado al objeto derivado de [CComModule](../../atl/reference/ccommodule-class.md)utilizado en este proyecto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

Contiene el BSTR asociado al `CComBSTR` objeto.

```
BSTR m_str;
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR:: Operator BSTR

Convierte un `CComBSTR` objeto en un BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Comentarios

Permite pasar `CComBSTR` objetos a funciones que tienen parámetros **BSTR [in]** .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComBSTR:: m_str](#m_str).

##  <a name="operator_not"></a>CComBSTR:: Operator!

Comprueba si la cadena BSTR es NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el miembro [m_str](#m_str) es null; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este operador solo comprueba si hay un valor NULL, no para una cadena vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>  CComBSTR::operator !=

Devuelve el opuesto lógico del [operador = =](#operator_eq_eq).

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
de Cadena terminada en cero.

*nNull*<br/>
de Debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se va a comparar no es `CComBSTR` igual al objeto; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

`CComBSTR`los s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. El operador de comparación final simplemente compara la cadena contenida con NULL.

##  <a name="operator_amp"></a>CComBSTR:: Operator&amp;

Devuelve la dirección del BSTR almacenado en el miembro [m_str](#m_str) .

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Comentarios

`CComBstr operator &`tiene asociada una aserción especial para ayudar a identificar pérdidas de memoria. El programa se validará cuando `m_str` se inicialice el miembro. Esta aserción se creó para identificar las situaciones en las `& operator` que un programador utiliza para asignar un nuevo valor a `m_str` un miembro sin liberar la primera asignación `m_str`de. Si `m_str` es igual a NULL, el programa supone que todavía no se ha asignado m_str. En este caso, el programa no se validará.

Esta aserción no está habilitada de forma predeterminada. Defina ATL_CCOMBSTR_ADDRESS_OF_ASSERT para habilitar esta aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>  CComBSTR::operator +=

Anexa una cadena al `CComBSTR` objeto.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parámetros

*bstrSrc*<br/>
de `CComBSTR` Objeto que se va a anexar.

*pszSrc*<br/>
de Cadena terminada en cero que se va a anexar.

### <a name="remarks"></a>Comentarios

`CComBSTR`los s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. La comparación de LPCOLESTR se realiza `memcmp` utilizando en los datos sin procesar de cada cadena. La comparación de LPCSTR se realiza de la misma manera una vez que se ha creado una copia temporal de *pszSrc* . El operador de comparación final simplemente compara la cadena contenida con NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR:: Operator&lt;

`CComBSTR` Compara con una cadena.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se está comparando `CComBSTR` es menor que el objeto; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

La comparación se realiza mediante la configuración regional predeterminada del usuario.

##  <a name="operator_eq"></a>  CComBSTR::operator =

Establece el miembro [m_str](#m_str) en una copia de *pSrc* o en una copia del miembro BSTR de *src*. El operador de asignación de `src` movimiento se mueve sin copiarlo.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Comentarios

El parámetro *pSrc* especifica un LPCOLESTR para las versiones Unicode o LPCSTR para las versiones ANSI.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CComBSTR:: Copy](#copy).

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

`CComBSTR` Compara con una cadena. `CComBSTR`los s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario.

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
de Cadena terminada en cero.

*nNull*<br/>
de Debe ser NULL.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se va a comparar es `CComBSTR` igual al objeto; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

El operador de comparación final simplemente compara la cadena contenida con NULL.

##  <a name="operator_gt"></a>CComBSTR:: Operator&gt;

`CComBSTR` Compara con una cadena.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se va a comparar es `CComBSTR` mayor que el objeto; de lo contrario, devuelve false.

### <a name="remarks"></a>Comentarios

La comparación se realiza mediante la configuración regional predeterminada del usuario.

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

Establece el miembro [m_str](#m_str) en el BSTR contenido en la secuencia especificada.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
de Un puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en la secuencia que contiene los datos.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`ReadToStream`requiere que el contenido de la secuencia en la posición actual sea compatible con el formato de datos escrito por una llamada a [WriteToStream](#writetostream).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

Convierte la cadena contenida en minúsculas.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Vea `CharLowerBuff` para obtener más información sobre cómo se realiza la conversión.

##  <a name="toupper"></a>  CComBSTR::ToUpper

Convierte la cadena contenida en mayúsculas.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Vea `CharUpperBuff` para obtener más información sobre cómo se realiza la conversión.

##  <a name="writetostream"></a>  CComBSTR::WriteToStream

Guarda el miembro [m_str](#m_str) en una secuencia.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parámetros

*pStream*<br/>
de Puntero a la interfaz [IStream](/windows/win32/api/objidl/nn-objidl-istream) en una secuencia.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Puede volver a crear un BSTR a partir del contenido de la secuencia mediante la función [ReadFromStream](#readfromstream) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[Macros de conversión de cadenas de ATL y MFC](string-conversion-macros.md)
