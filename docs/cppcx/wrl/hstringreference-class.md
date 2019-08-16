---
title: HStringReference (Clase)
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: 591af0d66c9c209ba56310a0bd5cf5cd74e34929
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498346"
---
# <a name="hstringreference-class"></a>HStringReference (Clase)

Representa un HSTRING que se crea a partir de una cadena existente.

## <a name="syntax"></a>Sintaxis

```cpp
class HStringReference;
```

## <a name="remarks"></a>Comentarios

La duración del búfer de respaldo en el nuevo HSTRING no está administrada por el Windows Runtime. El autor de la llamada asigna una cadena de origen en el marco de pila para evitar una asignación de montón y eliminar el riesgo de una fuga de memoria. Además, el llamador debe asegurarse de que la cadena de origen permanezca inalterada durante la vigencia del HSTRING adjunto. Para obtener más información, consulte [función WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

NOMBRE                                                    | DESCRIPCIÓN
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Inicializa una nueva instancia de la clase `HStringReference`.

### <a name="public-methods"></a>Métodos públicos

Member                              | DESCRIPCIÓN
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Copia el objeto `HStringReference` actual en un objeto HSTRING.
[HStringReference::Get](#get)       | Recupera el valor del identificador HSTRING subyacente.
[HStringReference::GetRawBuffer](#getrawbuffer) | Recupera un puntero a los datos de cadena subyacentes.

### <a name="public-operators"></a>Operadores públicos

NOMBRE                                                  | DESCRIPCIÓN
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | Mueve el valor de otro `HStringReference` objeto al objeto actual `HStringReference` .
[HStringReference::operator==](#operator-equality)    | Indica si los dos parámetros son iguales.
[HStringReference::operator!=](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HStringReference::operator&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HStringReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="copyto"></a>HStringReference::CopyTo

Copia el objeto `HStringReference` actual en un objeto HSTRING.

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

## <a name="get"></a>HStringReference::Get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

Valor del identificador HSTRING subyacente.

## <a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Recupera un puntero a los datos de cadena subyacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parámetros

*longitud* Puntero a una variable **int** que recibe la longitud de los datos.

### <a name="return-value"></a>Valor devuelto

Un puntero **const** a los datos de cadena subyacentes.

## <a name="hstringreference"></a>HStringReference::HStringReference

Inicializa una nueva instancia de la clase `HStringReference`.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parámetros

*sizeDest*<br/>
Parámetro de plantilla que especifica el tamaño del búfer de `HStringReference` destino.

*str*<br/>
Referencia a una cadena de caracteres anchos.

*len*<br/>
Longitud máxima del búfer de parámetros *Str* que se va a usar en esta operación. Si no se especifica el parámetro *Len* , se usa el parámetro *Str* completo. Si *Len* es mayor que el *tamaño*máximo, *Len* se establece en *size*-1.

*other*<br/>
Otro `HStringReference` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa un nuevo `HStringReference` objeto que tiene el mismo tamaño que el parámetro *Str*.

El segundo constructor inicializa un nuevo `HStringReference` objeto con el tamaño specifeid por el parámetro *Len*.

El tercer constructor inicializa un nuevo `HStringReference` objeto en el valor del *otro* parámetro y, a continuación, destruye el *otro* parámetro.

## <a name="operator-assign"></a>HStringReference::operator=

Mueve el valor de otro `HStringReference` objeto al objeto actual `HStringReference` .

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `HStringReference` existente.

### <a name="remarks"></a>Comentarios

El valor del *otro* objeto existente se copia en el objeto actual `HStringReference` y, a continuación, se destruye el *otro* objeto.

## <a name="operator-equality"></a>HStringReference::operator==

Indica si los dos parámetros son iguales.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser un `HStringReference` objeto o un identificador de HSTRING.

*rhs*<br/>
Segundo parámetro que se va a comparar.  *RHS* puede ser un `HStringReference` objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los parámetros *LHS* y *RHS* son iguales; en caso contrario, **false**.

## <a name="operator-inequality"></a>HStringReference::operator!=

Indica si los dos parámetros no son iguales.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser un `HStringReference` objeto o un identificador de HSTRING.

*rhs*<br/>
Segundo parámetro que se va a comparar.  *RHS* puede ser un `HStringReference` objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los parámetros *LHS* y *RHS* no son iguales; en caso contrario, **false**.

## <a name="operator-less-than"></a>HStringReference::operator&lt;

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*lhs*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser una referencia a `HStringReference`.

*rhs*<br/>
Segundo parámetro que se va a comparar.  *RHS* puede ser una referencia a `HStringReference`.

### <a name="return-value"></a>Valor devuelto

**true** si el parámetro *LHS* es menor que el parámetro *RHS* ; en caso contrario, **false**.
