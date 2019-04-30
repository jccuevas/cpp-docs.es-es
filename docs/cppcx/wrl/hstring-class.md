---
title: HString (Clase)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
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
ms.openlocfilehash: 19ef11a5d33e69bb77049e450df1b386528b7f7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398295"
---
# <a name="hstring-class"></a>HString (Clase)

Una clase auxiliar para administrar la duración de un [HSTRING](/windows/desktop/WinRT/hstring) con el patrón RAII.

## <a name="syntax"></a>Sintaxis

```cpp
class HString;
```

## <a name="remarks"></a>Comentarios

El tiempo de ejecución de Windows proporciona acceso a las cadenas a través de [HSTRING](/windows/desktop/WinRT/hstring) identificadores. La `HString` clase proporciona funciones de comodidad y operadores para simplificar el uso de identificadores de HSTRING. Esta clase puede controlar la duración de HSTRING posee a través de un modelo RAII.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                | Descripción
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inicializa una nueva instancia de la clase `HString`.
[HString::~HString](#tilde-hstring) | Destruye la instancia actual de la `HString` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                     | Descripción
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Asocia especificado `HString` objeto con el actual `HString` objeto.
[HString::CopyTo](#copyto)               | Copia actual `HString` objeto a un objeto HSTRING.
[HString::Detach](#detach)               | Anula la asociación entre `HString` objetos desde su valor subyacente.
[HString::Get](#get)                     | Recupera el valor del identificador HSTRING subyacente.
[HString::GetAddressOf](#getaddressof)   | Recupera un puntero al identificador HSTRING subyacente.
[HString::IsValid](#isvalid)             | Indica si el actual `HString` objeto es válido.
[HString::MakeReference](#makereference) | Crea un `HStringReference` objeto a partir de un parámetro de cadena especificado.
[HString::Release](#release)             | Elimina el valor de cadena subyacente e inicializa actual `HString` objeto en un valor vacío.
[HString::Set](#set)                     | Establece el valor del elemento actual `HString` objeto en la cadena especificada de caracteres anchos o `HString` parámetro.

### <a name="public-operators"></a>Operadores públicos

Name                                         | Descripción
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | Mueve el valor de otro `HString` el objeto actual `HString` objeto.
[HString::operator==](#operator-equality)    | Indica si los dos parámetros son iguales.
[HString::operator!=](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HString::operator&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HString`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString::~HString

Destruye la instancia actual de la `HString` clase.

```cpp
~HString() throw()
```

## <a name="attach"></a>HString::Attach

Asocia especificado `HString` objeto con el actual `HString` objeto.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parámetros

*hstr*<br/>
Objeto `HString` existente.

## <a name="copyto"></a>HString::CopyTo

Copia actual `HString` objeto a un objeto HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parámetros

*str*<br/>
La HSTRING que recibe la copia.

### <a name="remarks"></a>Comentarios

Este método llama a la [WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring) función.

## <a name="detach"></a>HString::Detach

Anula la asociación entre `HString` objetos desde su valor subyacente.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Valor devuelto

Subyacente `HString` valor antes de iniciar la operación de desasociación.

## <a name="get"></a>HString::Get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

El valor de identificador HSTRING subyacente

## <a name="getaddressof"></a>HString::GetAddressOf

Recupera un puntero al identificador HSTRING subyacente.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Valor devuelto

Puntero al identificador HSTRING subyacente.

### <a name="remarks"></a>Comentarios

Después de realizar esta operación, se destruye el valor de cadena del identificador HSTRING subyacente.

## <a name="hstring"></a>HString::HString

Inicializa una nueva instancia de la clase `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parámetros

*hstr*<br/>
Un identificador HSTRING.

*other*<br/>
Objeto `HString` existente.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa un nuevo `HString` objeto que está vacía.

El segundo constructor inicializa una nueva `HString` objeto por el valor de la existente *otros* parámetro y, a continuación, se destruye el *otros* parámetro.

## <a name="isvalid"></a>HString::IsValid

Indica si el actual `HString` objeto está vacío o no.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parámetros

**True** si actual `HString` objeto no está vacío; en caso contrario, **false**.

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
Un parámetro de plantilla que especifica el tamaño del destino `HStringReference` búfer.

*str*<br/>
Una referencia a una cadena de caracteres anchos.

*len*<br/>
La longitud máxima de la *str* búfer de parámetro para utilizar en esta operación. Si el *len* parámetro no se especifica, toda la *str* se usa el parámetro.

### <a name="return-value"></a>Valor devuelto

Un `HStringReference` objeto cuyo valor es igual que el especificado *str* parámetro.

## <a name="operator-assign"></a>Hstring:: operator = (operador)

Mueve el valor de otro `HString` el objeto actual `HString` objeto.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `HString` existente.

### <a name="remarks"></a>Comentarios

El valor de la existente *otros* objeto se copia a la actual `HString` objeto y, a continuación, el *otros* se destruye el objeto.

## <a name="operator-equality"></a>Hstring:: operator == (operador)

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
El primer parámetro para comparar. *LHS* puede ser un `HString` o `HStringReference` objeto o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro para comparar. *rhs* puede ser un `HString` o `HStringReference` objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**True** si el *lhs* y *rhs* parámetros son iguales; en caso contrario, **false**.

## <a name="operator-inequality"></a>Hstring:: operator! = (operador)

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
El primer parámetro para comparar. *LHS* puede ser un `HString` o `HStringReference` objeto o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro para comparar. *rhs* puede ser un `HString` o `HStringReference` objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**True** si el *lhs* y *rhs* parámetros no son iguales; en caso contrario, **false**.

## <a name="operator-less-than"></a>Hstring:: operator&lt; operador

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
El primer parámetro para comparar. *LHS* puede ser una referencia a un `HString`.

*rhs*<br/>
El segundo parámetro para comparar. *RHS* puede ser una referencia a un `HString`.

### <a name="return-value"></a>Valor devuelto

**True** si el *lhs* parámetro es menor que el *rhs* parámetro; en caso contrario, **false**.

## <a name="release"></a>HString::Release

Elimina el valor de cadena subyacente e inicializa actual `HString` objeto en un valor vacío.

```cpp
void Release() throw()
```

## <a name="set"></a>HString::Set

Establece el valor del elemento actual `HString` objeto en la cadena especificada de caracteres anchos o `HString` parámetro.

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
La longitud máxima de la *str* parámetro que se asigna a la actual `HString` objeto.

*hstr*<br/>
Objeto `HString` existente.
