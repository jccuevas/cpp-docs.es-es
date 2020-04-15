---
title: Clase CSimpleStringT
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: dce33289699b9e7b7484d1feb6335476f93dee9b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317686"
---
# <a name="csimplestringt-class"></a>Clase CSimpleStringT

Esta clase representa `CSimpleStringT` un objeto.

## <a name="syntax"></a>Sintaxis

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parámetros

*Basetype*<br/>
El tipo de carácter de la clase de cadena. Puede ser uno de los siguientes:

- **char** (para cadenas de caracteres ANSI).

- **wchar_t** (para cadenas de caracteres Unicode).

- TCHAR (para cadenas de caracteres ANSI y Unicode).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Un puntero a una cadena constante.|
|[CSimpleStringT::PXSTR](#pxstr)|Un puntero a una cadena.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Construye `CSimpleStringT` objetos de varias maneras.|
|[CSimpleStringT::-CSimpleStringT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|Anexa un `CSimpleStringT` objeto a `CSimpleStringT` un objeto existente.|
|[CSimpleStringT::AppendChar](#appendchar)|Anexa un carácter `CSimpleStringT` a un objeto existente.|
|[CSimpleStringT::CopyChars](#copychars)|Copia un carácter o caracteres en otra cadena.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copia un carácter o caracteres en otra cadena en la que los búferes se superponen.|
|[CSimpleStringT::Vacío](#empty)|Fuerza una cadena a tener una longitud de cero.|
|[CSimpleStringT::FreeExtra](#freeextra)|Libera cualquier memoria adicional previamente asignada por el objeto de cadena.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Recupera la longitud asignada `CSimpleStringT` de un objeto.|
|[CSimpleStringT::GetAt](#getat)|Devuelve el carácter en una posición determinada.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Devuelve un puntero a `CSimpleStringT`los caracteres de un archivo .|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Devuelve un puntero a `CSimpleStringT`los caracteres de un , truncando a la longitud especificada.|
|[CSimpleStringT::GetLength](#getlength)|Devuelve el número de `CSimpleStringT` caracteres de un objeto.|
|[CSimpleStringT::GetManager](#getmanager)|Recupera el administrador de `CSimpleStringT` memoria del objeto.|
|[CSimpleStringT::GetString](#getstring)|Recupera la cadena de caracteres|
|[CSimpleStringT::IsEmpty](#isempty)|Comprueba si `CSimpleStringT` un objeto no contiene caracteres.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Deshabilita el recuento de referencias y protege la cadena en el búfer.|
|[CSimpleStringT::Preallocate](#preallocate)|Asigna una cantidad específica de memoria para el búfer de caracteres.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Libera el control del `GetBuffer`búfer devuelto por .|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Libera el control del `GetBuffer`búfer devuelto por .|
|[CSimpleStringT::SetAt](#setat)|Establece un carácter en una posición determinada.|
|[CSimpleStringT::SetManager](#setmanager)|Establece el administrador `CSimpleStringT` de memoria de un objeto.|
|[CSimpleStringT::SetString](#setstring)|Establece la cadena `CSimpleStringT` de un objeto.|
|[CSimpleStringT::StringLength](#stringlength)|Devuelve el número de caracteres de la cadena especificada.|
|[CSimpleStringT::Truncate](#truncate)|Trunca la cadena a una longitud especificada.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Habilita el recuento de referencias y libera la cadena en el búfer.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT::operador PCXSTR](#operator_pcxstr)|Accede directamente a `CSimpleStringT` los caracteres almacenados en un objeto como una cadena de estilo C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Devuelve el carácter en una `GetAt`posición determinada — sustitución del operador para .|
|[CSimpleStringT::operador +o](#operator_add_eq)|Concatena una nueva cadena hasta el final de una cadena existente.|
|[CSimpleStringT::operator ?](#operator_eq)|Asigna un nuevo valor `CSimpleStringT` a un objeto.|

### <a name="remarks"></a>Observaciones

`CSimpleStringT`es la clase base para las diversas clases de cadena admitidas por Visual C++. Proporciona una compatibilidad mínima para la administración de memoria del objeto de cadena y la manipulación básica del búfer. Para obtener objetos de cadena más avanzados, vea [CStringT (Clase)](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT::Append

Anexa un `CSimpleStringT` objeto a `CSimpleStringT` un objeto existente.

### <a name="syntax"></a>Sintaxis

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parámetros

*strSrc*<br/>
El `CSimpleStringT` objeto que se va a anexar.

*pszSrc*<br/>
Puntero a una cadena que contiene los caracteres que se van a anexar.

*nLongitud*<br/>
Número de caracteres que se van a anexar.

### <a name="remarks"></a>Observaciones

Llame a este método `CSimpleStringT` para `CSimpleStringT` anexar un objeto existente a otro objeto.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar

Anexa un carácter `CSimpleStringT` a un objeto existente.

### <a name="syntax"></a>Sintaxis

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parámetros

*Ch*<br/>
El carácter a añadir

### <a name="remarks"></a>Observaciones

Llame a esta función para anexar el `CSimpleStringT` carácter especificado al final de un objeto existente.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

Copia un carácter `CSimpleStringT` o caracteres en un objeto.

### <a name="syntax"></a>Sintaxis

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parámetros

*pchDest*<br/>
Un puntero a una cadena de caracteres.

*pchSrc*<br/>
Puntero a una cadena que contiene los caracteres que se van a copiar.

*nChars*<br/>
El número de caracteres *pchSrc* que se van a copiar.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar caracteres de *pchSrc* a la cadena *pchDest.*

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Copia un carácter `CSimpleStringT` o caracteres en un objeto.

### <a name="syntax"></a>Sintaxis

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parámetros

*pchDest*<br/>
Un puntero a una cadena de caracteres.

*pchSrc*<br/>
Puntero a una cadena que contiene los caracteres que se van a copiar.

*nChars*<br/>
El número de caracteres *pchSrc* que se van a copiar.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar caracteres de *pchSrc* a la cadena *pchDest.* A `CopyChars` `CopyCharsOverlapped` diferencia de , proporciona un método seguro para copiar desde búferes de caracteres que podrían superponerse.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CSimpleStringT::CopyChars](#copychars)o `CSimpleStringT::SetString` el código fuente para (ubicado en atlsimpstr.h).

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT

Construye un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parámetros

*strSrc*<br/>
Objeto `CSimpleStringT` existente que se va `CSimpleStringT` a copiar en este objeto.

*pchSrc*<br/>
Un puntero a una matriz de caracteres de longitud *nLength*, no null terminado.

*pszSrc*<br/>
Cadena terminada en null que se `CSimpleStringT` va a copiar en este objeto.

*nLongitud*<br/>
Un recuento del número `pch`de caracteres en .

*pStringMgr*<br/>
Un puntero al administrador `CSimpleStringT` de memoria del objeto. Para obtener `IAtlStringMgr` más información `CSimpleStringT`acerca de la administración de memoria y la administración de memoria para , vea Administración de [memoria y CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Observaciones

Construye un nuevo objeto `CSimpleStringT`. Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, pueden producirse excepciones de memoria.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente `CSimpleStringT::CSimpleStringT` se muestra el uso de mediante el uso de la propiedad de **tipo** `CSimpleString`ATL . `CSimpleString`es una especialización comúnmente `CSimpleStringT`utilizada de la plantilla de clase.

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT::Vacío

Convierte `CSimpleStringT` este objeto en una cadena vacía y libera memoria según corresponda.

### <a name="syntax"></a>Sintaxis

```
void Empty() throw();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea Cadenas: Limpieza de [excepciones de CString](../cstring-exception-cleanup.md).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

Libera cualquier memoria adicional asignada previamente por la cadena, pero ya no es necesaria.

### <a name="syntax"></a>Sintaxis

```
void FreeExtra();
```

### <a name="remarks"></a>Observaciones

Esto debería reducir la sobrecarga de memoria consumida por el objeto de cadena. El método reasigna el búfer a la longitud exacta devuelta por [GetLength](#getlength).

### <a name="example"></a>Ejemplo

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>Observaciones

La salida de este ejemplo es la siguiente:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Recupera la longitud asignada `CSimpleStringT` de un objeto.

### <a name="syntax"></a>Sintaxis

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de caracteres asignados para este objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar `CSimpleStringT` el número de caracteres asignados para este objeto. Consulte [FreeExtra](#freeextra) para obtener un ejemplo de cómo llamar a esta función.

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT::GetAt

Devuelve un carácter de un `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
El índice de base cero `CSimpleStringT` del carácter del objeto. El parámetro *iChar* debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength). De `GetAt` lo contrario, generará una excepción.

### <a name="return-value"></a>Valor devuelto

Un `XCHAR` que contiene el carácter en la posición especificada en la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para devolver el carácter especificado por *iChar*. El operador de subíndice sobrecargado (**[]**) es un alias conveniente para `GetAt`. El terminador null es direccionable sin generar una excepción mediante `GetAt`. Sin embargo, no `GetLength`se cuenta por , y el valor devuelto es 0.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente `CSimpleStringT::GetAt`se muestra cómo utilizar .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT::GetBuffer

Devuelve un puntero al búfer `CSimpleStringT` de caracteres interno para el objeto.

### <a name="syntax"></a>Sintaxis

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parámetros

*nMinBufferLength*<br/>
El número mínimo de caracteres que puede contener el búfer de caracteres. Este valor no incluye espacio para un terminador nulo.

Si *nMinBufferLength* es mayor que la `GetBuffer` longitud del búfer actual, destruye el búfer actual, lo reemplaza por un búfer del tamaño solicitado y restablece el recuento de referencias de objeto a cero. Si anteriormente ha llamado a [LockBuffer](#lockbuffer) en este búfer, perderá el bloqueo del búfer.

### <a name="return-value"></a>Valor devuelto

Un `PXSTR` puntero al búfer de caracteres (terminado en null) del objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para `CSimpleStringT` devolver el contenido del búfer del objeto. El `PXSTR` devuelto no es una constante `CSimpleStringT` y, por lo tanto, permite la modificación directa de los contenidos.

Si usa el puntero `GetBuffer` devuelto para cambiar el contenido de la cadena, debe llamar a [ReleaseBuffer](#releasebuffer) antes de usar cualquier otro `CSimpleStringT` método miembro.

La dirección `GetBuffer` devuelta por puede no `ReleaseBuffer` ser `CSimpleStringT` válida después de la llamada a porque las operaciones adicionales pueden hacer que el `CSimpleStringT` búfer se reasigna. El búfer no se reasigna si no `CSimpleStringT`cambia la longitud del archivo .

La memoria del búfer se `CSimpleStringT` libera automáticamente cuando se destruye el objeto.

Si realiza un seguimiento de la longitud de la cadena usted mismo, no debe anexar el carácter nulo de terminación. Sin embargo, debe especificar la longitud de `ReleaseBuffer`cadena final al liberar el búfer con . Si anexa un carácter nulo de terminación, debe pasar -1 (valor predeterminado) para la longitud. `ReleaseBuffer`a continuación, determina la longitud del búfer.

Si no hay memoria `GetBuffer` suficiente para satisfacer la solicitud, este método produce una CMemoryException*.

### <a name="example"></a>Ejemplo

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Devuelve un puntero al búfer `CSimpleStringT` de caracteres interno para el objeto, truncando o aumentando su longitud si es necesario para que coincida exactamente con la longitud especificada en *nLength*.

### <a name="syntax"></a>Sintaxis

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parámetros

*nLongitud*<br/>
El tamaño exacto `CSimpleStringT` del búfer de caracteres en caracteres.

### <a name="return-value"></a>Valor devuelto

Puntero `PXSTR` al búfer de caracteres (terminado en null) del objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar una longitud `CSimpleStringT` especificada del búfer interno del objeto. El `PXSTR` puntero devuelto no es **const** `CSimpleStringT` y, por lo tanto, permite la modificación directa de contenido.

Si usa el puntero devuelto por [GetBufferSetLength](#getbuffersetlength) para `ReleaseBuffer` cambiar el contenido `CsimpleStringT` de la `CSimpleStringT` cadena, llame para actualizar el estado interno de antes de usar cualquier otro método.

La dirección `GetBufferSetLength` devuelta por puede no `ReleaseBuffer` ser `CSimpleStringT` válida después de la llamada a porque las operaciones adicionales pueden hacer que el `CSimpleStringT` búfer se reasigna. El búfer no se reasigna si no `CSimpleStringT`cambia la longitud del archivo .

La memoria del búfer se `CSimpleStringT` libera automáticamente cuando se destruye el objeto.

Si realiza un seguimiento de la longitud de la cadena usted mismo, no anexe el carácter nulo de terminación. Debe especificar la longitud de cadena final `ReleaseBuffer`al liberar el búfer mediante . Si anexa un carácter nulo de `ReleaseBuffer`terminación al llamar a , `ReleaseBuffer`pase `ReleaseBuffer` -1 `strlen` (valor predeterminado) para la longitud a , y realizará un en el búfer para determinar su longitud.

Para obtener más información sobre el recuento de referencias, consulte los siguientes artículos:

- Administración de la duración de los [objetos a través](/windows/win32/com/managing-object-lifetimes-through-reference-counting) del recuento de referencias en el Windows SDK.

- [Implementación](/windows/win32/com/implementing-reference-counting) del recuento de referencias en el Windows SDK.

- [Reglas para administrar recuentos](/windows/win32/com/rules-for-managing-reference-counts) de referencias en el Windows SDK.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::GetBufferSetLength`.

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT::GetLength

Devuelve el número de `CSimpleStringT` caracteres del objeto.

### <a name="syntax"></a>Sintaxis

```
int GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un recuento de los caracteres de la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para devolver el número de caracteres en el objeto. El recuento no incluye un terminador nulo.

Para conjuntos de caracteres `GetLength` multibyte (MBCS), cuenta cada carácter de 8 bits; es decir, un byte de cliente potencial y de seguimiento en un carácter multibyte se cuentan como dos bytes. Consulte [FreeExtra](#freeextra) para obtener un ejemplo de cómo llamar a esta función.

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager

Recupera el administrador de `CSimpleStringT` memoria del objeto.

### <a name="syntax"></a>Sintaxis

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al administrador `CSimpleStringT` de memoria para el objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar `CSimpleStringT` el administrador de memoria utilizado por el objeto. Para obtener más información sobre los administradores de memoria y los objetos de cadena, vea [Administración de memoria y CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT::GetString

Recupera la cadena de caracteres.

### <a name="syntax"></a>Sintaxis

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena de caracteres terminada en null.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar `CSimpleStringT` la cadena de caracteres asociada al objeto.

> [!NOTE]
> El `PCXSTR` puntero devuelto es **const** y `CSimpleStringT` no permite la modificación directa del contenido.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT::IsEmpty

Comprueba `CSimpleStringT` un objeto para la condición vacía.

### <a name="syntax"></a>Sintaxis

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE `CSimpleStringT` si el objeto tiene 0 longitud; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar si el objeto contiene una cadena vacía.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Deshabilita el recuento de referencias y protege la cadena en el búfer.

### <a name="syntax"></a>Sintaxis

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Valor devuelto

Puntero a `CSimpleStringT` un objeto o una cadena terminada en null.

### <a name="remarks"></a>Observaciones

Llame a este método para `CSimpleStringT` bloquear el búfer del objeto. Al `LockBuffer`llamar a , se crea una copia de la cadena, con un -1 para el recuento de referencias. Cuando el valor de recuento de referencias es -1, se considera que la cadena del búfer está en un estado "bloqueado". Mientras está en un estado bloqueado, la cadena está protegida de dos maneras:

- Ninguna otra cadena puede obtener una referencia a los datos de la cadena bloqueada, incluso si esa cadena está asignada a la cadena bloqueada.

- La cadena bloqueada nunca hará referencia a otra cadena, incluso si esa otra cadena se copia en la cadena bloqueada.

Al bloquear la cadena en el búfer, se asegura de que la retención exclusiva de la cadena en el búfer permanecerá intacta.

Una vez que `LockBuffer`haya terminado con , llame a [UnlockBuffer](#unlockbuffer) para restablecer el recuento de referencias a 1.

> [!NOTE]
> Si llama a [GetBuffer](#getbuffer) en un `GetBuffer` búfer `nMinBufferLength` bloqueado y establece el parámetro en mayor que la longitud del búfer actual, perderá el bloqueo del búfer. Dicha llamada `GetBuffer` para destruir el búfer actual, lo reemplaza por un búfer del tamaño solicitado y restablece el recuento de referencias a cero.

Para obtener más información sobre el recuento de referencias, consulte los siguientes artículos:

- [Administración de la duración de los objetos mediante](/windows/win32/com/managing-object-lifetimes-through-reference-counting) el recuento de referencias en el Windows SDK

- [Implementación del recuento](/windows/win32/com/implementing-reference-counting) de referencias en el Windows SDK

- [Reglas para administrar recuentos](/windows/win32/com/rules-for-managing-reference-counts) de referencias en el Windows SDK

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]

Llame a esta función para tener acceso a un solo carácter de la matriz de caracteres.

### <a name="syntax"></a>Sintaxis

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
El índice de base cero de un carácter de la cadena.

### <a name="remarks"></a>Observaciones

El operador de subíndice sobrecargado (**[]**) devuelve un único carácter especificado por el índice de base cero en *iChar*. Este operador es un sustituto conveniente para el [GetAt](#getat) función miembro.

> [!NOTE]
> Puede utilizar el operador subíndice (**[]**) para `CSimpleStringT`obtener el valor de un carácter en `CSimpleStringT`un , pero no se puede utilizar para cambiar el valor de un carácter en un archivo .

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]

Llame a esta función para tener acceso a un solo carácter de la matriz de caracteres.

### <a name="syntax"></a>Sintaxis

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parámetros

*iChar*<br/>
El índice de base cero de un carácter de la cadena.

### <a name="remarks"></a>Observaciones

El operador de subíndice sobrecargado (**[]**) devuelve un único carácter especificado por el índice de base cero en *iChar*. Este operador es un sustituto conveniente para el [GetAt](#getat) función miembro.

> [!NOTE]
> Puede utilizar el operador subíndice (**[]**) para `CSimpleStringT`obtener el valor de un carácter en `CSimpleStringT`un , pero no se puede utilizar para cambiar el valor de un carácter en un archivo .

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::operador +o

Une una nueva cadena o carácter al final de una cadena existente.

### <a name="syntax"></a>Sintaxis

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Puntero a una cadena terminada en null.

*strSrc*<br/>
Puntero a un `CSimpleStringT` objeto existente.

*Ch*<br/>
Carácter que se va a anexar.

### <a name="remarks"></a>Observaciones

El operador acepta `CSimpleStringT` otro objeto o un carácter. Tenga en cuenta que pueden producirse excepciones de memoria siempre que utilice `CSimpleStringT` este operador de concatenación porque se puede asignar nuevo almacenamiento para los caracteres agregados a este objeto.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::operator ?

Asigna un nuevo valor `CSimpleStringT` a un objeto.

### <a name="syntax"></a>Sintaxis

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Puntero a una cadena terminada en null.

*strSrc*<br/>
Puntero a un `CSimpleStringT` objeto existente.

### <a name="remarks"></a>Observaciones

Si la cadena de destino (el lado izquierdo) ya es lo suficientemente grande como para almacenar los nuevos datos, no se realiza ninguna nueva asignación de memoria. Tenga en cuenta que pueden producirse excepciones de memoria siempre que `CSimpleStringT` utilice el operador de asignación porque a menudo se asigna nuevo almacenamiento para contener el objeto resultante.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator =`.

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT::operador PCXSTR

Accede directamente a `CSimpleStringT` los caracteres almacenados en un objeto como una cadena de estilo C.

### <a name="syntax"></a>Sintaxis

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero de carácter a los datos de la cadena.

### <a name="remarks"></a>Observaciones

No se copia ningún carácter; solo se devuelve un puntero. Tenga cuidado con este operador. Si cambia `CString` un objeto después de haber obtenido el puntero de carácter, puede provocar una reasignación de memoria que invalide el puntero.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator PCXSTR`.

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR

Un puntero a una cadena constante.

### <a name="syntax"></a>Sintaxis

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::Preallocate

Asigna una cantidad específica de `CSimpleStringT` bytes para el objeto.

### <a name="syntax"></a>Sintaxis

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parámetros

*nLongitud*<br/>
El tamaño exacto `CSimpleStringT` del búfer de caracteres en caracteres.

### <a name="remarks"></a>Observaciones

Llame a este método para asignar `CSimpleStringT` un tamaño de búfer específico para el objeto.

`CSimpleStringT`genera una excepción STATUS_NO_MEMORY si no puede asignar espacio para el búfer de caracteres. De forma predeterminada, la asignación de `HeapAlloc` `HeapReAlloc`memoria se realiza mediante funciones de API WIN32 o .

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::PXSTR

Un puntero a una cadena.

### <a name="syntax"></a>Sintaxis

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Libera el control del búfer asignado por [GetBuffer](#getbuffer).

### <a name="syntax"></a>Sintaxis

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La nueva longitud de la cadena en caracteres, sin contar un terminador nulo. Si la cadena es null terminated, el `CSimpleStringT` valor predeterminado -1 establece el tamaño en la longitud actual de la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para reasignar o liberar el búfer del objeto de cadena. Si sabe que la cadena del búfer es null terminated, puede omitir el *argumento nNewLength.* Si la cadena no termina en null, utilice *nNewLength* para especificar su longitud. La dirección devuelta por [GetBuffer](#getbuffer) `ReleaseBuffer` no es `CSimpleStringT` válida después de la llamada o cualquier otra operación.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::ReleaseBuffer`.

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Libera el control del búfer asignado por [GetBuffer](#getbuffer).

### <a name="syntax"></a>Sintaxis

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La longitud de la cadena que se libera

### <a name="remarks"></a>Observaciones

Esta función es funcionalmente similar a [ReleaseBuffer,](#releasebuffer) excepto que se debe pasar una longitud válida para el objeto de cadena.

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::SetAt

Establece un único `CSimpleStringT` carácter de un objeto.

### <a name="syntax"></a>Sintaxis

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
El índice de base cero `CSimpleStringT` del carácter del objeto. El parámetro *iChar* debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength).

*Ch*<br/>
El nuevo personaje.

### <a name="remarks"></a>Observaciones

Llame a este método para sobrescribir el carácter ubicado en *iChar*. Este método no ampliará la cadena si *iChar* supera los límites de la cadena existente.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager

Especifica el administrador de `CSimpleStringT` memoria del objeto.

### <a name="syntax"></a>Sintaxis

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parámetros

*pStringMgr*<br/>
Un puntero al nuevo administrador de memoria.

### <a name="remarks"></a>Observaciones

Llame a este método para especificar `CSimpleStringT` un nuevo administrador de memoria utilizado por el objeto. Para obtener más información sobre los administradores de memoria y los objetos de cadena, vea [Administración de memoria y CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT::SetString

Establece la cadena `CSimpleStringT` de un objeto.

### <a name="syntax"></a>Sintaxis

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Puntero a una cadena terminada en null.

*nLongitud*<br/>
Un recuento del número de caracteres en *pszSrc*.

### <a name="remarks"></a>Observaciones

Copie una cadena `CSimpleStringT` en el objeto. `SetString`sobrescribe los datos de cadena más antiguos en el búfer.

Ambas versiones de `SetString` comprobación si *pszSrc* es un puntero nulo y, si lo es, producir un error de E_INVALIDARG.

La versión de `SetString` un parámetro de espera *pszSrc* para apuntar a una cadena terminada en null.

La versión de `SetString` dos parámetros de también espera *pszSrc* para ser una cadena terminada en null. Utiliza *nLength* como la longitud de cadena a menos que encuentre primero un terminador nulo.

La versión de `SetString` dos parámetros de también comprueba si *pszSrc* apunta a una ubicación en el búfer actual en `CSimpleStringT`. En este caso `SetString` especial, utiliza una función de copia de memoria que no sobrescribe los datos de cadena, ya que copia los datos de cadena en su búfer.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT::StringLength

Devuelve el número de caracteres de la cadena especificada.

### <a name="syntax"></a>Sintaxis

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parámetros

*psz*<br/>
Puntero a una cadena terminada en null.

### <a name="return-value"></a>Valor devuelto

El número de caracteres en *psz*; sin contar un terminador nulo.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de caracteres de la cadena señalada por *psz*.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::Truncate

Trunca la cadena a la nueva longitud.

### <a name="syntax"></a>Sintaxis

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La nueva longitud de la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para truncar el contenido de la cadena a la nueva longitud.

> [!NOTE]
> Esto no afecta a la longitud asignada del búfer. Para reducir o aumentar el búfer actual, consulte [FreeExtra](#freeextra) y [Preallocate](#preallocate).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Desbloquea el búfer `CSimpleStringT` del objeto.

### <a name="syntax"></a>Sintaxis

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Observaciones

Llame a este método para restablecer el recuento de referencias de la cadena a 1.

El `CSimpleStringT` destructor `UnlockBuffer` llama automáticamente para asegurarse de que el búfer no está bloqueado cuando se llama al destructor. Para obtener un ejemplo de este método, vea [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT::-CSimpleStringT

Destruye un objeto `CSimpleStringT` .

### <a name="syntax"></a>Sintaxis

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Observaciones

Llame a este `CSimpleStringT` método para destruir el objeto.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
