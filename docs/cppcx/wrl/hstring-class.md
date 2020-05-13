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
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371432"
---
# <a name="hstring-class"></a>HString (Clase)

Una clase auxiliar para administrar la duración de un [HSTRING](/windows/win32/WinRT/hstring) mediante el patrón RAII.

## <a name="syntax"></a>Sintaxis

```cpp
class HString;
```

## <a name="remarks"></a>Observaciones

Windows Runtime proporciona acceso a cadenas a través de identificadores [HSTRING.](/windows/win32/WinRT/hstring) La `HString` clase proporciona funciones de conveniencia y operadores para simplificar el uso de identificadores HSTRING. Esta clase puede controlar la duración de la HSTRING que posee a través de un patrón RAII.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                | Descripción
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inicializa una nueva instancia de la clase `HString`.
[HString::-HString](#tilde-hstring) | Destruye la instancia actual `HString` de la clase.

### <a name="public-methods"></a>Métodos públicos

Nombre                                     | Descripción
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Asocia el `HString` objeto especificado `HString` con el objeto actual.
[HString::CopyTo](#copyto)               | Copia el `HString` objeto actual en un objeto HSTRING.
[HString::Detach](#detach)               | Desasocia el `HString` objeto especificado de su valor subyacente.
[HString::Get](#get)                     | Recupera el valor del identificador HSTRING subyacente.
[HString::GetAddressOf](#getaddressof)   | Recupera un puntero al identificador HSTRING subyacente.
[HString::GetRawBuffer](#getrawbuffer)   | Recupera un puntero a los datos de cadena subyacentes.
[HString::IsValid](#isvalid)             | Indica si el `HString` objeto actual es válido.
[HString::MakeReference](#makereference) | Crea `HStringReference` un objeto a partir de un parámetro de cadena especificado.
[HString::Release](#release)             | Elimina el valor de cadena subyacente e intiliziza el objeto actual `HString` en un valor vacío.
[HString::Set](#set)                     | Establece el valor `HString` del objeto actual en la `HString` cadena o parámetro de caracteres anchos especificado.

### <a name="public-operators"></a>Operadores públicos

Nombre                                         | Descripción
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operador ?](#operator-assign)       | Mueve el valor `HString` de otro `HString` objeto al objeto actual.
[HString::operador](#operator-equality)    | Indica si los dos parámetros son iguales.
[HString::operador!](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HString::operador&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HString`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString::-HString

Destruye la instancia actual `HString` de la clase.

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString::Attach

Asocia el `HString` objeto especificado `HString` con el objeto actual.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parámetros

*hstr*<br/>
Objeto `HString` existente.

## <a name="hstringcopyto"></a><a name="copyto"></a>HString::CopyTo

Copia el `HString` objeto actual en un objeto HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
El HSTRING que recibe la copia.

### <a name="remarks"></a>Observaciones

Este método llama a la función [WindowsDuplicateString.](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)

## <a name="hstringdetach"></a><a name="detach"></a>HString::Detach

Desasocia el `HString` objeto especificado de su valor subyacente.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Valor devuelto

El valor `HString` subyacente antes de que se iniciara la operación de desasociación.

## <a name="hstringget"></a><a name="get"></a>HString::Get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

El valor del identificador HSTRING subyacente

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString::GetAddressOf

Recupera un puntero al identificador HSTRING subyacente.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Valor devuelto

Un puntero al identificador HSTRING subyacente.

### <a name="remarks"></a>Observaciones

Después de esta operación, se destruye el valor de cadena del identificador HSTRING subyacente.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString::GetRawBuffer

Recupera un puntero a los datos de cadena subyacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parámetros

*longitud* Puntero a una variable **int** que recibe la longitud de los datos.

### <a name="return-value"></a>Valor devuelto

Un **puntero const** a los datos de cadena subyacentes.

## <a name="hstringhstring"></a><a name="hstring"></a>HString::HString

Inicializa una nueva instancia de la clase `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parámetros

*hstr*<br/>
Un identificador HSTRING.

*Otro*<br/>
Objeto `HString` existente.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa `HString` un nuevo objeto que está vacío.

El segundo constructor inicializa `HString` un nuevo objeto en el valor del *otro* parámetro existente y, a continuación, destruye el *otro* parámetro.

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString::IsValid

Indica si el `HString` objeto actual está vacío o no.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parámetros

**true** si `HString` el objeto actual no está vacío; de lo contrario, **false**.

## <a name="hstringmakereference"></a><a name="makereference"></a>HString::MakeReference

Crea `HStringReference` un objeto a partir de un parámetro de cadena especificado.

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
Un parámetro de plantilla que especifica `HStringReference` el tamaño del búfer de destino.

*Str*<br/>
Una referencia a una cadena de caracteres anchos.

*Len*<br/>
La longitud máxima del búfer de *parámetros str* que se va a utilizar en esta operación. Si no se especifica el parámetro *len,* se utiliza todo el parámetro *str.*

### <a name="return-value"></a>Valor devuelto

Objeto `HStringReference` cuyo valor es el mismo que el parámetro *str* especificado.

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString::operador- Operador

Mueve el valor `HString` de otro `HString` objeto al objeto actual.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Objeto `HString` existente.

### <a name="remarks"></a>Observaciones

El valor del *otro* objeto existente se `HString` copia en el objeto actual y, a continuación, se destruye el *otro* objeto.

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString::operador - Operador

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

*Lhs*<br/>
El primer parámetro que se va a comparar. *lhs* puede `HString` ser `HStringReference` un objeto u o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro que se va a comparar. *rhs* puede `HString` ser `HStringReference` un objeto u, o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los *parámetros lhs* y *rhs* son iguales; de lo contrario, **false**.

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString::operator!

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

*Lhs*<br/>
El primer parámetro que se va a comparar. *lhs* puede `HString` ser `HStringReference` un objeto u o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro que se va a comparar. *rhs* puede `HString` ser `HStringReference` un objeto u, o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los *parámetros lhs* y *rhs* no son iguales; de lo contrario, **false**.

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString::operador&lt; Operador

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El primer parámetro que se va a comparar. *lhs* puede ser una `HString`referencia a un archivo .

*rhs*<br/>
El segundo parámetro que se va a comparar. *rhs* puede ser una `HString`referencia a un archivo .

### <a name="return-value"></a>Valor devuelto

**true** si el parámetro *lhs* es menor que el parámetro *rhs;* de lo contrario, **false**.

## <a name="hstringrelease"></a><a name="release"></a>HString::Release

Elimina el valor de cadena subyacente e intiliziza el objeto actual `HString` en un valor vacío.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString::Set

Establece el valor `HString` del objeto actual en la `HString` cadena o parámetro de caracteres anchos especificado.

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

*Str*<br/>
Una cadena de caracteres anchos.

*Len*<br/>
La longitud máxima del parámetro *str* asignado `HString` al objeto actual.

*hstr*<br/>
Objeto `HString` existente.
