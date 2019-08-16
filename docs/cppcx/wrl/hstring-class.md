---
title: HString (Clase)
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 71ebc02dc56b45e8790bfac7b7d4bac80d5f7729
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500496"
---
# <a name="hstring-class"></a>HString (Clase)

Una clase auxiliar para administrar la duración de un [HSTRING](/windows/win32/WinRT/hstring) con el patrón RAII.

## <a name="syntax"></a>Sintaxis

```cpp
class HString;
```

## <a name="remarks"></a>Comentarios

El Windows Runtime proporciona acceso a las cadenas a través de los identificadores de [HSTRING](/windows/win32/WinRT/hstring) . La `HString` clase proporciona funciones y operadores útiles para simplificar el uso de identificadores de HSTRING. Esta clase puede controlar la duración del HSTRING que posee a través de un patrón RAII.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

NOMBRE                                | DESCRIPCIÓN
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inicializa una nueva instancia de la clase `HString`.
[HString::~HString](#tilde-hstring) | Destruye la instancia actual de la `HString` clase.

### <a name="public-methods"></a>Métodos públicos

NOMBRE                                     | DESCRIPCIÓN
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Asocia el objeto `HString` especificado al objeto actual `HString` .
[HString::CopyTo](#copyto)               | Copia el objeto `HString` actual en un objeto HSTRING.
[HString::Detach](#detach)               | Desasocia el objeto especificado `HString` de su valor subyacente.
[HString::Get](#get)                     | Recupera el valor del identificador HSTRING subyacente.
[HString::GetAddressOf](#getaddressof)   | Recupera un puntero al identificador HSTRING subyacente.
[HString::GetRawBuffer](#getrawbuffer)   | Recupera un puntero a los datos de cadena subyacentes.
[HString::IsValid](#isvalid)             | Indica si el objeto `HString` actual es válido.
[HString::MakeReference](#makereference) | Crea un `HStringReference` objeto a partir de un parámetro de cadena especificado.
[HString::Release](#release)             | Elimina el valor de cadena subyacente y inicializa el objeto `HString` actual a un valor vacío.
[HString::Set](#set)                     | Establece el valor del objeto actual `HString` en la cadena de caracteres anchos o `HString` el parámetro especificados.

### <a name="public-operators"></a>Operadores públicos

NOMBRE                                         | DESCRIPCIÓN
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | Mueve el valor de otro `HString` objeto al objeto actual `HString` .
[HString::operator==](#operator-equality)    | Indica si los dos parámetros son iguales.
[HString::operator!=](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HString::operator&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HString`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString::~HString

Destruye la instancia actual de la `HString` clase.

```cpp
~HString() throw()
```

## <a name="attach"></a>HString:: Attach

Asocia el objeto `HString` especificado al objeto actual `HString` .

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parámetros

*hstr*<br/>
Objeto `HString` existente.

## <a name="copyto"></a>HString::CopyTo

Copia el objeto `HString` actual en un objeto HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parámetros

*str*<br/>
HSTRING que recibe la copia.

### <a name="remarks"></a>Comentarios

Este método llama a la función [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) .

## <a name="detach"></a>HString::Detach

Desasocia el objeto especificado `HString` de su valor subyacente.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Valor devuelto

Valor subyacente `HString` antes de que se inicie la operación de desasociación.

## <a name="get"></a>HString::Get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

Valor del identificador HSTRING subyacente.

## <a name="getaddressof"></a>HString::GetAddressOf

Recupera un puntero al identificador HSTRING subyacente.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Valor devuelto

Puntero al identificador de HSTRING subyacente.

### <a name="remarks"></a>Comentarios

Después de esta operación, se destruye el valor de cadena del identificador HSTRING subyacente.

## <a name="getrawbuffer"></a>HString::GetRawBuffer

Recupera un puntero a los datos de cadena subyacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parámetros

*longitud* Puntero a una variable **int** que recibe la longitud de los datos.

### <a name="return-value"></a>Valor devuelto

Un puntero **const** a los datos de cadena subyacentes.


## <a name="hstring"></a>HString::HString

Inicializa una nueva instancia de la clase `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parámetros

*hstr*<br/>
Identificador de HSTRING.

*other*<br/>
Objeto `HString` existente.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa un nuevo `HString` objeto que está vacío.

El segundo constructor inicializa un nuevo `HString` objeto con el valor del *otro* parámetro existente y, a continuación, destruye el *otro* parámetro.

## <a name="isvalid"></a>HString::IsValid

Indica si el objeto `HString` actual está vacío o no.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parámetros

**true** si el objeto `HString` actual no está vacío; en caso contrario, **false**.

## <a name="makereference"></a>HString::MakeReference

Crea un `HStringReference` objeto a partir de un parámetro de cadena especificado.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parámetros

*sizeDest*<br/>
Parámetro de plantilla que especifica el tamaño del búfer de `HStringReference` destino.

*str*<br/>
Referencia a una cadena de caracteres anchos.

*len*<br/>
Longitud máxima del búfer de parámetros *Str* que se va a usar en esta operación. Si no se especifica el parámetro *Len* , se usa el parámetro *Str* completo.

### <a name="return-value"></a>Valor devuelto

Objeto cuyo valor es el mismo que el parámetro Str especificado. `HStringReference`

## <a name="operator-assign"></a>HString:: Operator = (operador)

Mueve el valor de otro `HString` objeto al objeto actual `HString` .

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `HString` existente.

### <a name="remarks"></a>Comentarios

El valor del *otro* objeto existente se copia en el objeto actual `HString` y, a continuación, se destruye el *otro* objeto.

## <a name="operator-equality"></a>HString:: Operator = = (operador)

Indica si los dos parámetros son iguales.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser un `HString` objeto `HStringReference` o o un identificador HSTRING.

*rhs*<br/>
Segundo parámetro que se va a comparar. *RHS* puede ser un `HString` objeto `HStringReference` o o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los parámetros *LHS* y *RHS* son iguales; en caso contrario, **false**.

## <a name="operator-inequality"></a>HString:: Operator! = (operador)

Indica si los dos parámetros no son iguales.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser un `HString` objeto `HStringReference` o o un identificador HSTRING.

*rhs*<br/>
Segundo parámetro que se va a comparar. *RHS* puede ser un `HString` objeto `HStringReference` o o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los parámetros *LHS* y *RHS* no son iguales; en caso contrario, **false**.

## <a name="operator-less-than"></a>HString:: Operator&lt; (operador)

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser una referencia a `HString`.

*rhs*<br/>
Segundo parámetro que se va a comparar. *RHS* puede ser una referencia a `HString`.

### <a name="return-value"></a>Valor devuelto

**true** si el parámetro *LHS* es menor que el parámetro *RHS* ; en caso contrario, **false**.

## <a name="release"></a>HString:: Release

Elimina el valor de cadena subyacente y inicializa el objeto `HString` actual a un valor vacío.

```cpp
void Release() throw()
```

## <a name="set"></a>HString::Set

Establece el valor del objeto actual `HString` en la cadena de caracteres anchos o `HString` el parámetro especificados.

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Una cadena de caracteres anchos.

*len*<br/>
La longitud máxima del parámetro *Str* que se asigna al objeto actual `HString` .

*hstr*<br/>
Objeto `HString` existente.
