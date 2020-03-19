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
ms.openlocfilehash: 34a2f0530d33eb61ac50b65dc1ae123d5ea5a0be
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509489"
---
# <a name="hstringreference-class"></a>HStringReference (Clase)

Representa un HSTRING que se crea a partir de una cadena existente.

## <a name="syntax"></a>Sintaxis

```cpp
class HStringReference;
```

## <a name="remarks"></a>Observaciones

La duración del búfer de respaldo en el nuevo HSTRING no está administrada por el Windows Runtime. El autor de la llamada asigna una cadena de origen en el marco de pila para evitar una asignación de montón y eliminar el riesgo de una fuga de memoria. Además, el llamador debe asegurarse de que la cadena de origen permanezca inalterada durante la vigencia del HSTRING adjunto. Para obtener más información, consulte [función WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                    | Descripción
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference:: HStringReference](#hstringreference) | Inicializa una nueva instancia de la clase `HStringReference`.

### <a name="public-methods"></a>Métodos públicos

Member                              | Descripción
----------------------------------- | ------------------------------------------------------------------
[HStringReference:: CopyTo](#copyto) | Copia el objeto de `HStringReference` actual en un objeto HSTRING.
[HStringReference:: get](#get)       | Recupera el valor del identificador HSTRING subyacente.
[HStringReference:: GetRawBuffer](#getrawbuffer) | Recupera un puntero a los datos de cadena subyacentes.

### <a name="public-operators"></a>Operadores públicos

Nombre                                                  | Descripción
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference:: Operator =](#operator-assign)       | Mueve el valor de otro objeto `HStringReference` al objeto `HStringReference` actual.
[HStringReference:: Operator = =](#operator-equality)    | Indica si los dos parámetros son iguales.
[HStringReference:: Operator! =](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HStringReference:: Operator&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HStringReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

**Espacio de nombres:** Microsoft:: WRL:: wrappers

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference:: CopyTo

Copia el objeto de `HStringReference` actual en un objeto HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parámetros

*str*<br/>
HSTRING que recibe la copia.

### <a name="remarks"></a>Observaciones

Este método llama a la función [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) .

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference:: get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

Valor del identificador HSTRING subyacente.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference:: GetRawBuffer

Recupera un puntero a los datos de cadena subyacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parámetros

*longitud* Puntero a una variable **int** que recibe la longitud de los datos.

### <a name="return-value"></a>Valor devuelto

Un puntero **const** a los datos de cadena subyacentes.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference:: HStringReference

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

*Tamaño más*<br/>
Parámetro de plantilla que especifica el tamaño del búfer de `HStringReference` de destino.

*str*<br/>
Referencia a una cadena de caracteres anchos.

*len*<br/>
Longitud máxima del búfer de parámetros *Str* que se va a usar en esta operación. Si no se especifica el parámetro *Len* , se usa el parámetro *Str* completo. Si *Len* es mayor que el *tamaño*máximo, *Len* se establece en *size*-1.

*other*<br/>
Otro objeto de `HStringReference`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa un nuevo objeto `HStringReference` que tiene el mismo tamaño que el parámetro *Str*.

El segundo constructor inicializa un nuevo objeto `HStringReference` que el tamaño specifeid por el parámetro *Len*.

El tercer constructor inicializa un nuevo objeto `HStringReference` en el valor del *otro* parámetro y, a continuación, destruye el *otro* parámetro.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference:: Operator =

Mueve el valor de otro objeto `HStringReference` al objeto `HStringReference` actual.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Objeto `HStringReference` existente.

### <a name="remarks"></a>Observaciones

El valor del *otro* objeto existente se copia en el objeto `HStringReference` actual y, a continuación, se destruye el *otro* objeto.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference:: Operator = =

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

*LHS*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser un objeto `HStringReference` o un identificador HSTRING.

*rhs*<br/>
Segundo parámetro que se va a comparar.  *RHS* puede ser un objeto `HStringReference` o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los parámetros *LHS* y *RHS* son iguales; en caso contrario, **false**.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference:: Operator! =

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

*LHS*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser un objeto `HStringReference` o un identificador HSTRING.

*rhs*<br/>
Segundo parámetro que se va a comparar.  *RHS* puede ser un objeto `HStringReference` o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los parámetros *LHS* y *RHS* no son iguales; en caso contrario, **false**.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference:: Operator&lt;

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*LHS*<br/>
Primer parámetro que se va a comparar. *LHS* puede ser una referencia a una `HStringReference`.

*rhs*<br/>
Segundo parámetro que se va a comparar.  *RHS* puede ser una referencia a un `HStringReference`.

### <a name="return-value"></a>Valor devuelto

**true** si el parámetro *LHS* es menor que el parámetro *RHS* ; en caso contrario, **false**.
