---
title: CSimpleStringT (clase)
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
ms.openlocfilehash: 93cb3ae0b2f358f64f0d6de26899d1b08f275b7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579288"
---
# <a name="csimplestringt-class"></a>CSimpleStringT (clase)

Esta clase representa un `CSimpleStringT` objeto.

## <a name="syntax"></a>Sintaxis

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parámetros

*BaseType*<br/>
El tipo de carácter de la clase string. Puede ser uno de los siguientes:

- **char** (para las cadenas de caracteres ANSI).

- **wchar_t** (para cadenas de caracteres Unicode).

- TCHAR (para las cadenas de caracteres ANSI y Unicode).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Un puntero a una constante de cadena.|
|[CSimpleStringT::PXSTR](#pxstr)|Un puntero a una cadena.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Construye `CSimpleStringT` objetos de varias maneras.|
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|Anexa un `CSimpleStringT` objeto a una existente `CSimpleStringT` objeto.|
|[CSimpleStringT::AppendChar](#appendchar)|Anexa un carácter a un existente `CSimpleStringT` objeto.|
|[CSimpleStringT::CopyChars](#copychars)|Copia un carácter o caracteres en otra cadena.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copia un carácter o caracteres en otra cadena en la que se superponen los búferes.|
|[CSimpleStringT::Empty](#empty)|Fuerza una cadena con una longitud de cero.|
|[CSimpleStringT::FreeExtra](#freeextra)|Libera la memoria adicional asignado previamente mediante el objeto de cadena.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Recupera la longitud asignada de un `CSimpleStringT` objeto.|
|[CSimpleStringT::GetAt](#getat)|Devuelve el carácter que ocupa una posición especificada.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Devuelve un puntero a los caracteres de un `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Devuelve un puntero a los caracteres de un `CSimpleStringT`, se trunca a la longitud especificada.|
|[CSimpleStringT::GetLength](#getlength)|Devuelve el número de caracteres en un `CSimpleStringT` objeto.|
|[CSimpleStringT::GetManager](#getmanager)|Recupera el Administrador de memoria de la `CSimpleStringT` objeto.|
|[CSimpleStringT::GetString](#getstring)|Recupera la cadena de caracteres|
|[CSimpleStringT::IsEmpty](#isempty)|Las pruebas si un `CSimpleStringT` no contiene ningún carácter.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Deshabilita el recuento de referencias y protege la cadena en el búfer.|
|[CSimpleStringT::Preallocate](#preallocate)|Asigna una cantidad específica de memoria para el búfer de caracteres.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Devuelve el control del búfer devuelto por `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Devuelve el control del búfer devuelto por `GetBuffer`.|
|[CSimpleStringT::SetAt](#setat)|Establece un carácter en una posición determinada.|
|[CSimpleStringT::SetManager](#setmanager)|Establece el Administrador de memoria de un `CSimpleStringT` objeto.|
|[CSimpleStringT::SetString](#setstring)|Establece la cadena de un `CSimpleStringT` objeto.|
|[CSimpleStringT::StringLength](#stringlength)|Devuelve el número de caracteres de la cadena especificada.|
|[CSimpleStringT::Truncate](#truncate)|Trunca la cadena con una longitud especificada.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Permite el recuento de referencias y libera la cadena en el búfer.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Accede directamente a caracteres almacenados en un `CSimpleStringT` objeto como una cadena de estilo C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Devuelve el carácter que ocupa una posición determinada: sustitución de operador para `GetAt`.|
|[CSimpleStringT::operator +=](#operator_add_eq)|Concatena una nueva cadena al final de una cadena existente.|
|[CSimpleStringT::operator =](#operator_eq)|Asigna un nuevo valor a un `CSimpleStringT` objeto.|

### <a name="remarks"></a>Comentarios

`CSimpleStringT` es la clase base para las diferentes clases de cadenas compatible con Visual C++. Proporciona la compatibilidad mínima para la administración de memoria del objeto de cadena y la manipulación del búfer básica. Para los objetos de cadena más avanzados, consulte [clase CStringT](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr.h

## <a name="append"></a> CSimpleStringT::Append

Anexa un `CSimpleStringT` objeto a una existente `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parámetros

*strSrc*<br/>
La `CSimpleStringT` objeto se va a anexar.

*pszSrc*<br/>
Un puntero a una cadena que contiene los caracteres que se va a anexar.

*nLength*<br/>
Número de caracteres que se van a anexar.

### <a name="remarks"></a>Comentarios

Llame a este método para anexar una existente `CSimpleStringT` objeto a otro `CSimpleStringT` objeto.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a> CSimpleStringT::AppendChar

Anexa un carácter a un existente `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parámetros

*CH*<br/>
El carácter que se debe anexar

### <a name="remarks"></a>Comentarios

Llame a esta función para anexar el carácter especificado al final de una existente `CSimpleStringT` objeto.

##  <a name="copychars"></a> CSimpleStringT::CopyChars

Copia un carácter o caracteres que un `CSimpleStringT` objeto.

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
Un puntero a una cadena que contiene los caracteres que se va a copiar.

*nChars*<br/>
El número de *pchSrc* caracteres que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar los caracteres de *pchSrc* a la *pchDest* cadena.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>  CSimpleStringT::CopyCharsOverlapped

Copia un carácter o caracteres que un `CSimpleStringT` objeto.

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
Un puntero a una cadena que contiene los caracteres que se va a copiar.

*nChars*<br/>
El número de *pchSrc* caracteres que se va a copiar.

### <a name="remarks"></a>Comentarios

Llame a este método para copiar los caracteres de *pchSrc* a la *pchDest* cadena. A diferencia de `CopyChars`, `CopyCharsOverlapped` proporciona un método seguro para la copia de los búferes de caracteres que se pueden superponer.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CSimpleStringT::CopyChars](#copychars), o el código fuente de `CSimpleStringT::SetString` (ubicado en atlsimpstr.h).

##  <a name="ctor"></a>  CSimpleStringT::CSimpleStringT

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
Existente `CSimpleStringT` objeto que se copiará en esto `CSimpleStringT` objeto.

*pchSrc*<br/>
Un puntero a una matriz de caracteres de longitud *nLength*, no terminado en null.

*pszSrc*<br/>
Una cadena terminada en null que se copiará en esto `CSimpleStringT` objeto.

*nLength*<br/>
Un recuento del número de caracteres en `pch`.

*pStringMgr*<br/>
Un puntero para el Administrador de memoria de la `CSimpleStringT` objeto. Para obtener más información acerca de `IAtlStringMgr` y administración de memoria para `CSimpleStringT`, consulte [administración de memoria y CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Comentarios

Construye un nuevo objeto `CSimpleStringT`. Dado que los constructores copian los datos de entrada en el nuevo almacenamiento asignado, pueden producir excepciones de memoria.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de `CSimpleStringT::CSimpleStringT` mediante el uso de la biblioteca ATL **typedef** `CSimpleString`. `CSimpleString` es una especialización de la plantilla de clase frecuente `CSimpleStringT`.

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

##  <a name="empty"></a>  CSimpleStringT::Empty

Convierte esta `CSimpleStringT` una cadena vacía de objetos y libera memoria según corresponda.

### <a name="syntax"></a>Sintaxis

```
void Empty() throw();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [cadenas: limpieza de excepciones de CString](../cstring-exception-cleanup.md).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>  CSimpleStringT::FreeExtra

Libera la memoria previamente asignada por la cadena, pero ya no es necesario adicional.

### <a name="syntax"></a>Sintaxis

```
void FreeExtra();
```

### <a name="remarks"></a>Comentarios

Esto debería reducir la sobrecarga de memoria consumida por el objeto de cadena. El método reasigna el búfer para la longitud exacta devuelta por [GetLength](#getlength).

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

### <a name="remarks"></a>Comentarios

El resultado de este ejemplo es como sigue:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

##  <a name="getalloclength"></a>  CSimpleStringT::GetAllocLength

Recupera la longitud asignada de un `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

El número de caracteres asignados para este objeto.

### <a name="remarks"></a>Comentarios

Llame a este método para determinar el número de caracteres asignados a esta `CSimpleStringT` objeto. Consulte [FreeExtra](#freeextra) para obtener un ejemplo de una llamada a esta función.

##  <a name="getat"></a>  CSimpleStringT::GetAt

Devuelve un carácter de un `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero del carácter en el `CSimpleStringT` objeto. El *iChar* parámetro debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength). En caso contrario, `GetAt` generará una excepción.

### <a name="return-value"></a>Valor devuelto

Un `XCHAR` que contiene el carácter que ocupa la posición especificada en la cadena.

### <a name="remarks"></a>Comentarios

Llamar a este método para devolver el carácter especificado por *iChar*. El subíndice sobrecargado (**[]**) operador es un alias adecuado para `GetAt`. El terminador nulo es direccionable sin generar una excepción mediante el uso de `GetAt`. Sin embargo, no se cuentan por `GetLength`, y el valor devuelto es 0.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>  CSimpleStringT::GetBuffer

Devuelve un puntero al búfer de caracteres interno para el `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parámetros

*nMinBufferLength*<br/>
El número mínimo de caracteres que puede contener el búfer de caracteres. Este valor no incluye espacio para un terminador nulo.

Si *nMinBufferLength* es mayor que la longitud del búfer actual, `GetBuffer` destruye el búfer actual, lo reemplaza con un búfer del tamaño solicitado y restablece el recuento de referencias de objeto a cero. Si previamente ha llamado [LockBuffer](#lockbuffer) en este búfer, se pierde el bloqueo del búfer.

### <a name="return-value"></a>Valor devuelto

Un `PXSTR` puntero al búfer de caracteres (terminada en null) del objeto.

### <a name="remarks"></a>Comentarios

Llamar a este método para devolver el contenido del búfer de la `CSimpleStringT` objeto. El valor devuelto `PXSTR` no es una constante y, por tanto, permite la modificación directa de `CSimpleStringT` contenido.

Si usa el puntero devuelto por `GetBuffer` para cambiar el contenido de la cadena, se debe llamar a [ReleaseBuffer](#releasebuffer) antes de usar cualquier otra `CSimpleStringT` métodos miembro.

La dirección devuelta por `GetBuffer` pueden no ser válidas después de llamar a `ReleaseBuffer` porque adicionales `CSimpleStringT` operaciones pueden producir el `CSimpleStringT` búfer se asignen de nuevo. No se reasigna el búfer si no cambia la longitud de la `CSimpleStringT`.

La memoria del búfer es automáticamente libera cuando el `CSimpleStringT` se destruye el objeto.

Si realiza un seguimiento de la longitud de cadena usted mismo, no es necesario anexar el carácter nulo de terminación. Sin embargo, debe especificar la longitud de la cadena final al liberar el búfer con `ReleaseBuffer`. Si anexa un carácter nulo final, debe pasar -1 (valor predeterminado) para la longitud. `ReleaseBuffer` a continuación, determina la longitud del búfer.

Si no hay memoria suficiente para satisfacer la `GetBuffer` solicitar, este método produce una CMemoryException *.

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

##  <a name="getbuffersetlength"></a>  CSimpleStringT::GetBufferSetLength

Devuelve un puntero al búfer de caracteres interno para el `CSimpleStringT` objeto truncar o aumentar su longitud, si es necesario para coincidir exactamente con la longitud especificada en *nLength*.

### <a name="syntax"></a>Sintaxis

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parámetros

*nLength*<br/>
El tamaño exacto de la `CSimpleStringT` búfer de caracteres en caracteres.

### <a name="return-value"></a>Valor devuelto

Un `PXSTR` puntero al búfer de caracteres (terminada en null) del objeto.

### <a name="remarks"></a>Comentarios

Llame a este método para recuperar una longitud especificada del búfer interno de la `CSimpleStringT` objeto. El valor devuelto `PXSTR` puntero no es **const** lo que permite la modificación directa de `CSimpleStringT` contenido.

Si usa el puntero devuelto por [GetBufferSetLength](#getbuffersetlength) para cambiar el contenido de la cadena, llame a `ReleaseBuffer` para actualizar el estado interno de `CsimpleStringT` antes de usar cualquier otra `CSimpleStringT` métodos.

La dirección devuelta por `GetBufferSetLength` pueden no ser válidas después de llamar a `ReleaseBuffer` porque adicionales `CSimpleStringT` operaciones pueden producir el `CSimpleStringT` búfer se asignen de nuevo. No se reasigna el búfer si no cambia la longitud de la `CSimpleStringT`.

La memoria del búfer es automáticamente libera cuando el `CSimpleStringT` se destruye el objeto.

Si realiza un seguimiento de la longitud de cadena usted mismo, no se anexa el carácter nulo de terminación. Debe especificar la longitud de la cadena final al liberar el búfer mediante `ReleaseBuffer`. Si anexe un carácter nulo al llamar a `ReleaseBuffer`, pasa -1 (valor predeterminado) para la longitud a `ReleaseBuffer`, y `ReleaseBuffer` llevará a cabo una `strlen` en el búfer para determinar su longitud.

Para obtener más información sobre el recuento de referencias, consulte los artículos siguientes:

- [Administrar la duración de objeto a través de un recuento de referencias](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) en el SDK de Windows.

- [Implementación de recuento de referencias](/windows/desktop/com/implementing-reference-counting) en el SDK de Windows.

- [Reglas para la administración de recuentos de referencias](/windows/desktop/com/rules-for-managing-reference-counts) en el SDK de Windows.

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

##  <a name="getlength"></a>  CSimpleStringT::GetLength

Devuelve el número de caracteres en el `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
int GetLength() const throw();
```

### <a name="return-value"></a>Valor devuelto

Recuento de los caracteres de la cadena.

### <a name="remarks"></a>Comentarios

Llame a este método para devolver el número de caracteres en el objeto. El recuento no incluye un terminador nulo.

Para los juegos de caracteres multibyte (MBCS), `GetLength` recuentos de cada byte de 8 bits carácter; es decir, una inicial y final en un carácter multibyte se cuentan como dos bytes. Consulte [FreeExtra](#freeextra) para obtener un ejemplo de una llamada a esta función.

##  <a name="getmanager"></a>  CSimpleStringT::GetManager

Recupera el Administrador de memoria de la `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al administrador de memoria para el `CSimpleStringT` objeto.

### <a name="remarks"></a>Comentarios

Llame a este método para recuperar la memoria utilizado por el administrador la `CSimpleStringT` objeto. Para obtener más información sobre los administradores de memoria y objetos de cadena, vea [administración de memoria y CStringT](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>  CSimpleStringT::GetString

Recupera la cadena de caracteres.

### <a name="syntax"></a>Sintaxis

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a una cadena de caracteres terminada en null.

### <a name="remarks"></a>Comentarios

Llame a este método para recuperar la cadena de caracteres asociada con el `CSimpleStringT` objeto.

> [!NOTE]
>  El valor devuelto `PCXSTR` puntero es **const** y no permite la modificación directa de `CSimpleStringT` contenido.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>  CSimpleStringT::IsEmpty

Las pruebas un `CSimpleStringT` objeto para la condición vacía.

### <a name="syntax"></a>Sintaxis

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el `CSimpleStringT` objeto tiene 0 longitud; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a este método para determinar si el objeto contiene una cadena vacía.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>  CSimpleStringT::LockBuffer

Deshabilita el recuento de referencias y protege la cadena en el búfer.

### <a name="syntax"></a>Sintaxis

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CSimpleStringT` objeto o una cadena terminada en null.

### <a name="remarks"></a>Comentarios

Llame a este método para bloquear el búfer de la `CSimpleStringT` objeto. Mediante una llamada a `LockBuffer`, crear una copia de la cadena, con un valor de -1 para el recuento de referencias. Cuando el valor de recuento de referencia es -1, se considera que la cadena en el búfer está en un estado "bloqueado". Mientras esté en un estado bloqueado, la protección de la cadena de dos maneras:

- Ninguna otra cadena puede obtener una referencia a los datos en la cadena de bloqueado, incluso si esa cadena se asigna a la cadena de bloqueada.

- La cadena bloqueada nunca hará referencia a otra cadena, incluso si esa cadena otra se copia en la cadena bloqueada.

Mediante el bloqueo de la cadena en el búfer, se asegura de que se modificará suspensión exclusivo de la cadena en el búfer.

Cuando haya terminado con `LockBuffer`, llame a [UnlockBuffer](#unlockbuffer) para restablecer el recuento de referencias en 1.

> [!NOTE]
>  Si se llama a [GetBuffer](#getbuffer) en un búfer bloqueado y ha establecido la `GetBuffer` parámetro `nMinBufferLength` sea mayor que la longitud del búfer actual, perderá el bloqueo del búfer. Este tipo de llamada a `GetBuffer` destruye el búfer actual, lo reemplaza con un búfer del tamaño solicitado y restablece el recuento de referencias en cero.

Para obtener más información sobre el recuento de referencias, consulte los artículos siguientes:

- [Administrar la duración de objeto a través de un recuento de referencias](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) en el SDK de Windows

- [Implementación de recuento de referencias](/windows/desktop/com/implementing-reference-counting) en el SDK de Windows

- [Reglas para la administración de recuentos de referencias](/windows/desktop/com/rules-for-managing-reference-counts) en el SDK de Windows

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

##  <a name="operator_at"></a>  CSimpleStringT::operator\[\]

Llame a esta función para obtener acceso a un único carácter de la matriz de caracteres.

### <a name="syntax"></a>Sintaxis

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero de un carácter en la cadena.

### <a name="remarks"></a>Comentarios

El subíndice sobrecargado (**[]**) operador devuelve un único carácter especificado por el índice de base cero en *iChar*. Este operador es un sustituto cómodo para el [GetAt](#getat) función miembro.

> [!NOTE]
>  Puede usar el subíndice (**[]**) operador para obtener el valor de un carácter en una `CSimpleStringT`, pero no se puede usar para cambiar el valor de un carácter en una `CSimpleStringT`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>  CSimpleStringT::operator \[\]

Llame a esta función para obtener acceso a un único carácter de la matriz de caracteres.

### <a name="syntax"></a>Sintaxis

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero de un carácter en la cadena.

### <a name="remarks"></a>Comentarios

El subíndice sobrecargado (**[]**) operador devuelve un único carácter especificado por el índice de base cero en *iChar*. Este operador es un sustituto cómodo para el [GetAt](#getat) función miembro.

> [!NOTE]
>  Puede usar el subíndice (**[]**) operador para obtener el valor de un carácter en una `CSimpleStringT`, pero no se puede usar para cambiar el valor de un carácter en una `CSimpleStringT`.

##  <a name="operator_add_eq"></a>  CSimpleStringT::operator +=

Se une a una nueva cadena o un carácter al final de una cadena existente.

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
Un puntero a una cadena terminada en null.

*strSrc*<br/>
Un puntero a una existente `CSimpleStringT` objeto.

*CH*<br/>
Carácter que se va a anexar.

### <a name="remarks"></a>Comentarios

El operador acepta otro `CSimpleStringT` objeto o un carácter. Tenga en cuenta que la memoria pueden producir excepciones cada vez que utilice este operador de concatenación porque es posible que se asigna nuevo almacenamiento para los caracteres que se agregaron a este `CSimpleStringT` objeto.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>  CSimpleStringT::operator =

Asigna un nuevo valor a un `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Un puntero a una cadena terminada en null.

*strSrc*<br/>
Un puntero a una existente `CSimpleStringT` objeto.

### <a name="remarks"></a>Comentarios

Si la cadena de destino (el lado izquierdo) ya es suficientemente grande como para almacenar los nuevos datos, no se realiza ninguna nueva asignación de memoria. Tenga en cuenta que la memoria pueden producir excepciones cada vez que utilice el operador de asignación porque a menudo se asigna nuevo almacenamiento para contener resultante `CSimpleStringT` objeto.

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

##  <a name="operator_pcxstr"></a>  CSimpleStringT::operator PCXSTR

Accede directamente a caracteres almacenados en un `CSimpleStringT` objeto como una cadena de estilo C.

### <a name="syntax"></a>Sintaxis

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a los datos de la cadena de carácter.

### <a name="remarks"></a>Comentarios

No se copian caracteres; se devuelve solo un puntero. Tenga cuidado con este operador. Si cambia un `CString` objeto después de haber obtenido el puntero de carácter, puede provocar una reasignación de memoria que invalida el puntero.

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

##  <a name="pcxstr"></a>  CSimpleStringT::PCXSTR

Un puntero a una constante de cadena.

### <a name="syntax"></a>Sintaxis

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>  CSimpleStringT::Preallocate

Asigna una cantidad específica de bytes para el `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parámetros

*nLength*<br/>
El tamaño exacto de la `CSimpleStringT` búfer de caracteres en caracteres.

### <a name="remarks"></a>Comentarios

Llame a este método para asignar un tamaño de búfer específico para el `CSimpleStringT` objeto.

`CSimpleStringT` genera una excepción STATUS_NO_MEMORY si no puede asignar espacio para el búfer de caracteres. De forma predeterminada, la asignación de memoria se realiza mediante funciones de la API de WIN32 `HeapAlloc` o `HeapReAlloc`.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>  CSimpleStringT::PXSTR

Un puntero a una cadena.

### <a name="syntax"></a>Sintaxis

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>  CSimpleStringT::ReleaseBuffer

Devuelve el control del búfer asignado por [GetBuffer](#getbuffer).

### <a name="syntax"></a>Sintaxis

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La nueva longitud de la cadena en caracteres, sin contar un terminador nulo. Si la cadena termina en null, Establece el valor predeterminado de-1 la `CSimpleStringT` tamaño a la longitud actual de la cadena.

### <a name="remarks"></a>Comentarios

Llame a este método para reasignar o liberar el búfer del objeto de cadena. Si sabe que la cadena en el búfer está terminado en null, puede omitir el *nNewLength* argumento. Si la cadena no es null terminó, use *nNewLength* para especificar su longitud. La dirección devuelta por [GetBuffer](#getbuffer) no es válida después de llamar a `ReleaseBuffer` o cualquier otro `CSimpleStringT` operación.

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

##  <a name="releasebuffersetlength"></a>  CSimpleStringT::ReleaseBufferSetLength

Devuelve el control del búfer asignado por [GetBuffer](#getbuffer).

### <a name="syntax"></a>Sintaxis

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La longitud de la cadena de liberarse

### <a name="remarks"></a>Comentarios

Esta función es funcionalmente similar a [ReleaseBuffer](#releasebuffer) , salvo que se debe pasar una longitud válida para el objeto de cadena.

##  <a name="setat"></a>  CSimpleStringT::SetAt

Establece un solo carácter de un `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parámetros

*iChar*<br/>
Índice de base cero del carácter en el `CSimpleStringT` objeto. El *iChar* parámetro debe ser mayor o igual que 0 y menor que el valor devuelto por [GetLength](#getlength).

*CH*<br/>
El carácter de nueva.

### <a name="remarks"></a>Comentarios

Llame a este método para sobrescribir el carácter situado en *iChar*. Este método no ampliará la cadena si *iChar* supera los límites de la cadena existente.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>  CSimpleStringT::SetManager

Especifica el Administrador de memoria de la `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parámetros

*pStringMgr*<br/>
Un puntero para el nuevo administrador de memoria.

### <a name="remarks"></a>Comentarios

Llame a este método para especificar una nueva memoria usando el administrador la `CSimpleStringT` objeto. Para obtener más información sobre los administradores de memoria y objetos de cadena, vea [administración de memoria y CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>  CSimpleStringT::SetString

Establece la cadena de un `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parámetros

*pszSrc*<br/>
Un puntero a una cadena terminada en null.

*nLength*<br/>
Un recuento del número de caracteres en *pszSrc*.

### <a name="remarks"></a>Comentarios

Copiar una cadena en el `CSimpleStringT` objeto. `SetString` sobrescribe los datos más antiguos de la cadena en el búfer.

Ambas versiones de `SetString` comprobar si *pszSrc* es un puntero nulo y si es así, producir un error E_INVALIDARG.

La versión de un parámetro de `SetString` espera *pszSrc* para que apunte a una cadena terminada en null.

La versión de dos parámetros de `SetString` también espera *pszSrc* sea una cadena terminada en null. Lo usa *nLength* como la longitud de cadena a menos que encuentra en primer lugar un terminador nulo.

La versión de dos parámetros de `SetString` también comprueba si *pszSrc* apunta a una ubicación en el búfer actual en `CSimpleStringT`. En este caso especial, `SetString` usa una función de copia de memoria que no sobrescribe los datos de cadena mientras realiza la copia los datos de cadena a su búfer.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>  CSimpleStringT::StringLength

Devuelve el número de caracteres de la cadena especificada.

### <a name="syntax"></a>Sintaxis

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parámetros

*psz*<br/>
Un puntero a una cadena terminada en null.

### <a name="return-value"></a>Valor devuelto

El número de caracteres en *psz*; sin contar un terminador nulo.

### <a name="remarks"></a>Comentarios

Llame a este método para recuperar el número de caracteres de la cadena señalada por *psz*.

### <a name="example"></a>Ejemplo

El siguiente ejemplo muestra el uso de `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>  CSimpleStringT::Truncate

Trunca la cadena a la nueva longitud.

### <a name="syntax"></a>Sintaxis

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parámetros

*nNewLength*<br/>
La nueva longitud de la cadena.

### <a name="remarks"></a>Comentarios

Llame a este método para truncar el contenido de la cadena para la nueva longitud.

> [!NOTE]
>  Esto no afecta a la longitud del búfer asignada. Para aumentar o reducir el búfer actual, vea [FreeExtra](#freeextra) y [Preallocate](#preallocate).

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

##  <a name="unlockbuffer"></a>  CSimpleStringT::UnlockBuffer

Desbloquea el búfer de la `CSimpleStringT` objeto.

### <a name="syntax"></a>Sintaxis

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Comentarios

Llame a este método para restablecer el recuento de referencias de la cadena en 1.

El `CSimpleStringT` destructor llama automáticamente a `UnlockBuffer` para asegurarse de que el búfer no está bloqueado cuando se llama al destructor. Para obtener un ejemplo de este método, consulte [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>  CSimpleStringT:: ~ CSimpleStringT

Destruye un objeto `CSimpleStringT`.

### <a name="syntax"></a>Sintaxis

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Comentarios

Llame a este método para destruir el `CSimpleStringT` objeto.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)