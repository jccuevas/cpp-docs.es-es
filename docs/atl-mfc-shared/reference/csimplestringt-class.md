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
ms.openlocfilehash: c033346b7a687a1c6778ad23e30ee0e73c787ad8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865087"
---
# <a name="csimplestringt-class"></a>Clase CSimpleStringT

Esta clase representa un objeto de `CSimpleStringT`.

## <a name="syntax"></a>Sintaxis

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parámetros

*BaseType*<br/>
Tipo de carácter de la clase String. Puede ser uno de los siguientes:

- **Char** (para cadenas de caracteres ANSI).

- **wchar_t** (para cadenas de caracteres Unicode).

- TCHAR (para cadenas de caracteres ANSI y Unicode).

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT::P CXSTR](#pcxstr)|Puntero a una cadena de constante.|
|[CSimpleStringT::P XSTR](#pxstr)|Puntero a una cadena.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Construye objetos `CSimpleStringT` de varias maneras.|
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT:: Append](#append)|Anexa un objeto `CSimpleStringT` a un objeto `CSimpleStringT` existente.|
|[CSimpleStringT::AppendChar](#appendchar)|Anexa un carácter a un objeto de `CSimpleStringT` existente.|
|[CSimpleStringT::CopyChars](#copychars)|Copia un carácter o caracteres en otra cadena.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copia un carácter o caracteres en otra cadena en la que se superponen los búferes.|
|[CSimpleStringT:: Empty](#empty)|Fuerza que una cadena tenga una longitud de cero.|
|[CSimpleStringT::FreeExtra](#freeextra)|Libera cualquier memoria adicional asignada previamente por el objeto de cadena.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Recupera la longitud asignada de un objeto `CSimpleStringT`.|
|[CSimpleStringT:: GetAt](#getat)|Devuelve el carácter que se encuentra en una posición determinada.|
|[CSimpleStringT:: GetBuffer](#getbuffer)|Devuelve un puntero a los caracteres de un `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Devuelve un puntero a los caracteres de un `CSimpleStringT`, truncando la longitud especificada.|
|[CSimpleStringT:: GetLength](#getlength)|Devuelve el número de caracteres de un objeto `CSimpleStringT`.|
|[CSimpleStringT::GetManager](#getmanager)|Recupera el administrador de memoria del objeto `CSimpleStringT`.|
|[CSimpleStringT:: GetString](#getstring)|Recupera la cadena de caracteres.|
|[CSimpleStringT:: IsEmpty](#isempty)|Comprueba si un objeto de `CSimpleStringT` no contiene caracteres.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Deshabilita el recuento de referencias y protege la cadena en el búfer.|
|[CSimpleStringT::P reasignar](#preallocate)|Asigna una cantidad específica de memoria para el búfer de caracteres.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Libera el control del búfer devuelto por `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Libera el control del búfer devuelto por `GetBuffer`.|
|[CSimpleStringT:: SetAt](#setat)|Establece un carácter en una posición determinada.|
|[CSimpleStringT::SetManager](#setmanager)|Establece el administrador de memoria de un objeto `CSimpleStringT`.|
|[CSimpleStringT:: SetString](#setstring)|Establece la cadena de un objeto `CSimpleStringT`.|
|[CSimpleStringT:: StringLength](#stringlength)|Devuelve el número de caracteres de la cadena especificada.|
|[CSimpleStringT:: TRUNCATE](#truncate)|Trunca la cadena a una longitud especificada.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Habilita el recuento de referencias y libera la cadena en el búfer.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleStringT:: Operator PCXSTR](#operator_pcxstr)|Accede directamente a los caracteres almacenados en un objeto de `CSimpleStringT` como una cadena de estilo C.|
|[CSimpleStringT:: Operator\[\]](#operator_at)|Devuelve el carácter que se encuentra en una posición determinada: sustitución de operadores para `GetAt`.|
|[CSimpleStringT:: Operator + =](#operator_add_eq)|Concatena una nueva cadena al final de una cadena existente.|
|[CSimpleStringT:: Operator =](#operator_eq)|Asigna un nuevo valor a un objeto `CSimpleStringT`.|

### <a name="remarks"></a>Observaciones

`CSimpleStringT` es la clase base para las distintas clases de cadena admitidas C++por visual. Proporciona compatibilidad mínima con la administración de memoria del objeto de cadena y la manipulación del búfer básico. Para obtener más información sobre objetos de cadena, vea [CStringT (clase](../../atl-mfc-shared/reference/cstringt-class.md)).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr. h

## <a name="append"></a>CSimpleStringT:: Append

Anexa un objeto `CSimpleStringT` a un objeto `CSimpleStringT` existente.

### <a name="syntax"></a>Sintaxis

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parámetros

*strSrc*<br/>
Objeto de `CSimpleStringT` que se va a anexar.

*pszSrc*<br/>
Puntero a una cadena que contiene los caracteres que se van a anexar.

*nLength*<br/>
Número de caracteres que se van a anexar.

### <a name="remarks"></a>Observaciones

Llame a este método para anexar un objeto de `CSimpleStringT` existente a otro objeto `CSimpleStringT`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a>CSimpleStringT::AppendChar

Anexa un carácter a un objeto de `CSimpleStringT` existente.

### <a name="syntax"></a>Sintaxis

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parámetros

*Cam*<br/>
Carácter que se va a anexar.

### <a name="remarks"></a>Observaciones

Llame a esta función para anexar el carácter especificado al final de un objeto de `CSimpleStringT` existente.

##  <a name="copychars"></a>CSimpleStringT::CopyChars

Copia un carácter o caracteres en un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parámetros

*pchDest*<br/>
Puntero a una cadena de caracteres.

*pchSrc*<br/>
Puntero a una cadena que contiene los caracteres que se van a copiar.

*nChars*<br/>
Número de caracteres de *pchSrc* que se van a copiar.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar los caracteres de *pchSrc* en la cadena *pchDest* .

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Copia un carácter o caracteres en un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parámetros

*pchDest*<br/>
Puntero a una cadena de caracteres.

*pchSrc*<br/>
Puntero a una cadena que contiene los caracteres que se van a copiar.

*nChars*<br/>
Número de caracteres de *pchSrc* que se van a copiar.

### <a name="remarks"></a>Observaciones

Llame a este método para copiar los caracteres de *pchSrc* en la cadena *pchDest* . A diferencia de `CopyChars`, `CopyCharsOverlapped` proporciona un método seguro para copiar desde búferes de caracteres que podrían estar superpuestos.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CSimpleStringT:: CopyChars](#copychars)o el código fuente de `CSimpleStringT::SetString` (ubicado en atlsimpstr. h).

##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT

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
Objeto de `CSimpleStringT` existente que se va a copiar en este objeto `CSimpleStringT`.

*pchSrc*<br/>
Un puntero a una matriz de caracteres de longitud *nLength*, no terminados en NULL.

*pszSrc*<br/>
Una cadena terminada en null que se va a copiar en este objeto `CSimpleStringT`.

*nLength*<br/>
Recuento del número de caracteres de `pch`.

*pStringMgr*<br/>
Puntero al administrador de memoria del objeto `CSimpleStringT`. Para obtener más información sobre la `IAtlStringMgr` y la administración de memoria para `CSimpleStringT`, vea [Administración de memoria y CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Observaciones

Construye un nuevo objeto `CSimpleStringT`. Dado que los constructores copian los datos de entrada en un nuevo almacenamiento asignado, pueden producirse excepciones de memoria.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de `CSimpleStringT::CSimpleStringT` mediante el `CSimpleString`**typedef** de ATL. `CSimpleString` es una especialización utilizada comúnmente de la plantilla de clase `CSimpleStringT`.

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

##  <a name="empty"></a>CSimpleStringT:: Empty

Convierte este objeto `CSimpleStringT` en una cadena vacía y libera la memoria según corresponda.

### <a name="syntax"></a>Sintaxis

```
void Empty() throw();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [cadenas: limpieza de excepciones de CString](../cstring-exception-cleanup.md).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>CSimpleStringT::FreeExtra

Libera cualquier memoria adicional asignada previamente por la cadena pero que ya no se necesita.

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

##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Recupera la longitud asignada de un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Número de caracteres asignados para este objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar el número de caracteres asignados a este objeto `CSimpleStringT`. Vea [FreeExtra](#freeextra) para obtener un ejemplo de llamada a esta función.

##  <a name="getat"></a>CSimpleStringT:: GetAt

Devuelve un carácter de un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero del carácter del objeto `CSimpleStringT`. El parámetro *iChar* debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength). De lo contrario, `GetAt` generará una excepción.

### <a name="return-value"></a>Valor devuelto

`XCHAR` que contiene el carácter situado en la posición especificada de la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para devolver el carácter especificado por *iChar*. El operador de subíndice sobrecargado ( **[]** ) es un alias adecuado para `GetAt`. El terminador null es direccionable sin generar una excepción mediante `GetAt`. Sin embargo, no cuenta con `GetLength`, y el valor devuelto es 0.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>CSimpleStringT:: GetBuffer

Devuelve un puntero al búfer de caracteres interno para el objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parámetros

*nMinBufferLength*<br/>
Número mínimo de caracteres que puede contener el búfer de caracteres. Este valor no incluye espacio para un terminador nulo.

Si *nMinBufferLength* es mayor que la longitud del búfer actual, `GetBuffer` destruye el búfer actual, lo reemplaza por un búfer del tamaño solicitado y restablece el recuento de referencias de objeto a cero. Si previamente ha llamado a [LockBuffer](#lockbuffer) en este búfer, perderá el bloqueo del búfer.

### <a name="return-value"></a>Valor devuelto

`PXSTR` puntero al búfer de caracteres (terminado en null) del objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para devolver el contenido del búfer del objeto `CSimpleStringT`. El `PXSTR` devuelto no es una constante y, por tanto, permite la modificación directa del contenido de `CSimpleStringT`.

Si usa el puntero devuelto por `GetBuffer` para cambiar el contenido de la cadena, debe llamar a [ReleaseBuffer](#releasebuffer) antes de usar cualquier otro método de miembro `CSimpleStringT`.

Es posible que la dirección devuelta por `GetBuffer` no sea válida después de la llamada a `ReleaseBuffer` porque las operaciones de `CSimpleStringT` adicionales pueden hacer que el búfer de `CSimpleStringT` se vuelva a asignar. No se reasigna el búfer si no se cambia la longitud del `CSimpleStringT`.

La memoria del búfer se libera automáticamente cuando se destruye el objeto de `CSimpleStringT`.

Si realiza un seguimiento de la longitud de la cadena, no debe anexar el carácter nulo de terminación. Sin embargo, debe especificar la longitud de cadena final al liberar el búfer con `ReleaseBuffer`. Si anexa un carácter nulo de terminación, debe pasar-1 (valor predeterminado) para la longitud. a continuación, `ReleaseBuffer` determina la longitud del búfer.

Si no hay memoria suficiente para satisfacer la solicitud de `GetBuffer`, este método produce una CMemoryException *.

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

##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Devuelve un puntero al búfer de caracteres interno para el objeto `CSimpleStringT`, truncando o aumentando su longitud si es necesario para coincidir exactamente con la longitud especificada en *nLength*.

### <a name="syntax"></a>Sintaxis

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parámetros

*nLength*<br/>
Tamaño exacto del búfer de caracteres `CSimpleStringT` en caracteres.

### <a name="return-value"></a>Valor devuelto

`PXSTR` puntero al búfer de caracteres (terminado en null) del objeto.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar una longitud especificada del búfer interno del objeto `CSimpleStringT`. El puntero `PXSTR` devuelto no es **const** y, por tanto, permite la modificación directa del contenido de `CSimpleStringT`.

Si usa el puntero devuelto por [GetBufferSetLength](#getbuffersetlength) para cambiar el contenido de la cadena, llame a `ReleaseBuffer` para actualizar el estado interno de `CsimpleStringT` antes de usar cualquier otro método de `CSimpleStringT`.

Es posible que la dirección devuelta por `GetBufferSetLength` no sea válida después de la llamada a `ReleaseBuffer` porque las operaciones de `CSimpleStringT` adicionales pueden hacer que el búfer de `CSimpleStringT` se vuelva a asignar. El búfer no se reasigna si no cambia la longitud del `CSimpleStringT`.

La memoria del búfer se libera automáticamente cuando se destruye el objeto de `CSimpleStringT`.

Si realiza un seguimiento de la longitud de la cadena, no Anexe el carácter nulo de terminación. Debe especificar la longitud de cadena final al liberar el búfer mediante `ReleaseBuffer`. Si anexa un carácter nulo de terminación al llamar a `ReleaseBuffer`, Pass-1 (valor predeterminado) para que la longitud se `ReleaseBuffer`y `ReleaseBuffer` realizará una `strlen` en el búfer para determinar su longitud.

Para obtener más información sobre el recuento de referencias, consulte los siguientes artículos:

- [Administrar la duración de los objetos mediante el recuento de referencias](/windows/win32/com/managing-object-lifetimes-through-reference-counting) en el Windows SDK.

- [Implementación del recuento de referencias](/windows/win32/com/implementing-reference-counting) en el Windows SDK.

- [Reglas para administrar recuentos de referencias](/windows/win32/com/rules-for-managing-reference-counts) en el Windows SDK.

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

##  <a name="getlength"></a>CSimpleStringT:: GetLength

Devuelve el número de caracteres del objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
int GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Recuento de los caracteres de la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para devolver el número de caracteres del objeto. El recuento no incluye un terminador nulo.

En el caso de los juegos de caracteres multibyte (MBCS), `GetLength` cuenta cada carácter de 8 bits; es decir, un byte inicial y final de un carácter multibyte se cuentan como dos bytes. Vea [FreeExtra](#freeextra) para obtener un ejemplo de llamada a esta función.

##  <a name="getmanager"></a>CSimpleStringT::GetManager

Recupera el administrador de memoria del objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero al administrador de memoria para el objeto de `CSimpleStringT`.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el administrador de memoria utilizado por el objeto `CSimpleStringT`. Para obtener más información sobre los administradores de memoria y los objetos de cadena, vea [Administración de memoria y CStringT](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>CSimpleStringT:: GetString

Recupera la cadena de caracteres.

### <a name="syntax"></a>Sintaxis

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una cadena de caracteres terminada en NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar la cadena de caracteres asociada al objeto de `CSimpleStringT`.

> [!NOTE]
>  El puntero `PCXSTR` devuelto es **const** y no permite la modificación directa de contenido de `CSimpleStringT`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>CSimpleStringT:: IsEmpty

Prueba un objeto de `CSimpleStringT` para la condición vacía.

### <a name="syntax"></a>Sintaxis

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el objeto de `CSimpleStringT` tiene una longitud de 0; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método para determinar si el objeto contiene una cadena vacía.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Deshabilita el recuento de referencias y protege la cadena en el búfer.

### <a name="syntax"></a>Sintaxis

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CSimpleStringT` o una cadena terminada en NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para bloquear el búfer del objeto `CSimpleStringT`. Al llamar a `LockBuffer`, se crea una copia de la cadena, con un valor-1 para el recuento de referencias. Cuando el valor de recuento de referencias es-1, se considera que la cadena en el búfer está en un estado "bloqueado". En un estado bloqueado, la cadena se protege de dos maneras:

- Ninguna otra cadena puede obtener una referencia a los datos de la cadena bloqueada, aunque esa cadena esté asignada a la cadena bloqueada.

- La cadena bloqueada nunca hará referencia a otra cadena, incluso si esa otra cadena se copia en la cadena bloqueada.

Al bloquear la cadena en el búfer, se asegura de que la suspensión exclusiva de la cadena en el búfer permanezca intacta.

Una vez que haya terminado con `LockBuffer`, llame a [UnlockBuffer](#unlockbuffer) para restablecer el recuento de referencias en 1.

> [!NOTE]
>  Si llama a [getBuffer](#getbuffer) en un búfer bloqueado y establece el parámetro `GetBuffer` `nMinBufferLength` en un valor mayor que la longitud del búfer actual, perderá el bloqueo del búfer. Esta llamada a `GetBuffer` destruye el búfer actual, lo reemplaza por un búfer del tamaño solicitado y restablece el recuento de referencias en cero.

Para obtener más información sobre el recuento de referencias, consulte los siguientes artículos:

- [Administrar la duración de los objetos mediante el recuento de referencias](/windows/win32/com/managing-object-lifetimes-through-reference-counting) en el Windows SDK

- [Implementar el recuento de referencias](/windows/win32/com/implementing-reference-counting) en el Windows SDK

- [Reglas para administrar recuentos de referencias](/windows/win32/com/rules-for-managing-reference-counts) en el Windows SDK

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

##  <a name="operator_at"></a>CSimpleStringT:: Operator\[\]

Llame a esta función para tener acceso a un único carácter de la matriz de caracteres.

### <a name="syntax"></a>Sintaxis

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero de un carácter de la cadena.

### <a name="remarks"></a>Observaciones

El operador de subíndice sobrecargado ( **[]** ) devuelve un solo carácter especificado por el índice de base cero en *iChar*. Este operador es un sustituto adecuado para la función miembro [GetAd](#getat) .

> [!NOTE]
>  Puede usar el operador de subíndice ( **[]** ) para obtener el valor de un carácter en un `CSimpleStringT`, pero no puede usarlo para cambiar el valor de un carácter en un `CSimpleStringT`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>CSimpleStringT:: Operator \[\]

Llame a esta función para tener acceso a un único carácter de la matriz de caracteres.

### <a name="syntax"></a>Sintaxis

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero de un carácter de la cadena.

### <a name="remarks"></a>Observaciones

El operador de subíndice sobrecargado ( **[]** ) devuelve un solo carácter especificado por el índice de base cero en *iChar*. Este operador es un sustituto adecuado para la función miembro [GetAd](#getat) .

> [!NOTE]
>  Puede usar el operador de subíndice ( **[]** ) para obtener el valor de un carácter en un `CSimpleStringT`, pero no puede usarlo para cambiar el valor de un carácter en un `CSimpleStringT`.

##  <a name="operator_add_eq"></a>CSimpleStringT:: Operator + =

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
Puntero a una cadena terminada en NULL.

*strSrc*<br/>
Puntero a un objeto de `CSimpleStringT` existente.

*Cam*<br/>
Carácter que se va a anexar.

### <a name="remarks"></a>Observaciones

El operador acepta otro objeto `CSimpleStringT` o un carácter. Tenga en cuenta que pueden producirse excepciones de memoria cada vez que se usa este operador de concatenación, ya que se puede asignar un nuevo almacenamiento para los caracteres agregados a este objeto `CSimpleStringT`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>CSimpleStringT:: Operator =

Asigna un nuevo valor a un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Puntero a una cadena terminada en NULL.

*strSrc*<br/>
Puntero a un objeto de `CSimpleStringT` existente.

### <a name="remarks"></a>Observaciones

Si la cadena de destino (el lado izquierdo) ya es lo suficientemente grande como para almacenar los datos nuevos, no se realiza ninguna asignación de memoria nueva. Tenga en cuenta que se pueden producir excepciones de memoria cada vez que se usa el operador de asignación porque a menudo se asigna un nuevo almacenamiento para contener el objeto de `CSimpleStringT` resultante.

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

##  <a name="operator_pcxstr"></a>CSimpleStringT:: Operator PCXSTR

Accede directamente a los caracteres almacenados en un objeto de `CSimpleStringT` como una cadena de estilo C.

### <a name="syntax"></a>Sintaxis

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero de carácter a los datos de la cadena.

### <a name="remarks"></a>Observaciones

No se copia ningún carácter; solo se devuelve un puntero. Tenga cuidado con este operador. Si cambia un objeto de `CString` después de haber obtenido el puntero de carácter, puede provocar una reasignación de memoria que invalide el puntero.

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

##  <a name="pcxstr"></a>CSimpleStringT::P CXSTR

Puntero a una cadena de constante.

### <a name="syntax"></a>Sintaxis

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>CSimpleStringT::P reasignar

Asigna una cantidad específica de bytes para el objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parámetros

*nLength*<br/>
Tamaño exacto del búfer de caracteres `CSimpleStringT` en caracteres.

### <a name="remarks"></a>Observaciones

Llame a este método para asignar un tamaño de búfer específico para el objeto `CSimpleStringT`.

`CSimpleStringT` genera una excepción de STATUS_NO_MEMORY si no puede asignar espacio para el búfer de caracteres. De forma predeterminada, la asignación de memoria se realiza mediante las funciones de la API de WIN32 `HeapAlloc` o `HeapReAlloc`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>CSimpleStringT::P XSTR

Puntero a una cadena.

### <a name="syntax"></a>Sintaxis

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Libera el control del búfer asignado por [getBuffer](#getbuffer).

### <a name="syntax"></a>Sintaxis

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La nueva longitud de la cadena en caracteres, sin contar un terminador null. Si la cadena está terminada en null, el valor predeterminado-1 establece el tamaño de la `CSimpleStringT` en la longitud actual de la cadena.

### <a name="remarks"></a>Observaciones

Llame a este método para reasignar o liberar el búfer del objeto de cadena. Si sabe que la cadena en el búfer termina en null, puede omitir el argumento *nNewLength* . Si la cadena no termina en null, use *nNewLength* para especificar su longitud. La dirección devuelta por [getBuffer](#getbuffer) no es válida después de la llamada a `ReleaseBuffer` o a cualquier otra operación de `CSimpleStringT`.

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

##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Libera el control del búfer asignado por [getBuffer](#getbuffer).

### <a name="syntax"></a>Sintaxis

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
Longitud de la cadena que se va a liberar.

### <a name="remarks"></a>Observaciones

Esta función es funcionalmente similar a [ReleaseBuffer](#releasebuffer) , salvo que se debe pasar una longitud válida para el objeto de cadena.

##  <a name="setat"></a>CSimpleStringT:: SetAt

Establece un solo carácter de un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero del carácter del objeto `CSimpleStringT`. El parámetro *iChar* debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength).

*Cam*<br/>
El nuevo carácter.

### <a name="remarks"></a>Observaciones

Llame a este método para sobrescribir el carácter que se encuentra en *iChar*. Este método no ampliará la cadena si *iChar* supera los límites de la cadena existente.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>CSimpleStringT::SetManager

Especifica el administrador de memoria del objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parámetros

*pStringMgr*<br/>
Puntero al nuevo administrador de memoria.

### <a name="remarks"></a>Observaciones

Llame a este método para especificar un nuevo administrador de memoria utilizado por el objeto `CSimpleStringT`. Para obtener más información sobre los administradores de memoria y los objetos de cadena, vea [Administración de memoria y CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>CSimpleStringT:: SetString

Establece la cadena de un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Puntero a una cadena terminada en NULL.

*nLength*<br/>
Recuento del número de caracteres de *pszSrc*.

### <a name="remarks"></a>Observaciones

Copie una cadena en el objeto `CSimpleStringT`. `SetString` sobrescribe los datos de cadena más antiguos en el búfer.

Ambas versiones de `SetString` comprobar si *pszSrc* es un puntero nulo y, si es así, producir un error E_INVALIDARG.

La versión de un parámetro de `SetString` espera que *pszSrc* señale a una cadena terminada en NULL.

La versión de dos parámetros de `SetString` también espera que *pszSrc* sea una cadena terminada en NULL. Usa *nLength* como la longitud de la cadena a menos que encuentre primero un terminador null.

La versión de dos parámetros de `SetString` también comprueba si *pszSrc* apunta a una ubicación en el búfer actual en `CSimpleStringT`. En este caso especial, `SetString` usa una función de copia de memoria que no sobrescribe los datos de cadena a medida que copia los datos de cadena de nuevo en su búfer.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>CSimpleStringT:: StringLength

Devuelve el número de caracteres de la cadena especificada.

### <a name="syntax"></a>Sintaxis

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parámetros

*psz*<br/>
Puntero a una cadena terminada en NULL.

### <a name="return-value"></a>Valor devuelto

Número de caracteres de *PSZ*; sin contar un terminador null.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de caracteres de la cadena a la que apunta *PSZ*.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>CSimpleStringT:: TRUNCATE

Trunca la cadena con la nueva longitud.

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
>  Esto no afecta a la longitud asignada del búfer. Para reducir o aumentar el búfer actual, consulte [FreeExtra](#freeextra) y [preasignación](#preallocate).

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

##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Desbloquea el búfer del objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Observaciones

Llame a este método para restablecer el recuento de referencias de la cadena en 1.

El destructor `CSimpleStringT` llama automáticamente a `UnlockBuffer` para asegurarse de que el búfer no está bloqueado cuando se llama al destructor. Para obtener un ejemplo de este método, vea [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT

Destruye un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Observaciones

Llame a este método para destruir el objeto `CSimpleStringT`.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas de ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
