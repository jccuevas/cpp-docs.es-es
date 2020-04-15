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
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371422"
---
# <a name="hstringreference-class"></a>HStringReference (Clase)

Representa un HSTRING que se crea a partir de una cadena existente.

## <a name="syntax"></a>Sintaxis

```cpp
class HStringReference;
```

## <a name="remarks"></a>Observaciones

Windows Runtime no administra la duración del búfer de respaldo en el nuevo HSTRING. El autor de la llamada asigna una cadena de origen en el marco de pila para evitar una asignación de montón y eliminar el riesgo de una pérdida de memoria. Además, el llamador debe asegurarse de que la cadena de origen permanece sin cambios durante la duración de la HSTRING adjunta. Para obtener más información, vea [Función WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                                    | Descripción
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Inicializa una nueva instancia de la clase `HStringReference`.

### <a name="public-methods"></a>Métodos públicos

Member                              | Descripción
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Copia el `HStringReference` objeto actual en un objeto HSTRING.
[HStringReference::Get](#get)       | Recupera el valor del identificador HSTRING subyacente.
[HStringReference::GetRawBuffer](#getrawbuffer) | Recupera un puntero a los datos de cadena subyacentes.

### <a name="public-operators"></a>Operadores públicos

Nombre                                                  | Descripción
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator ?](#operator-assign)       | Mueve el valor `HStringReference` de otro `HStringReference` objeto al objeto actual.
[HStringReference::operador ?](#operator-equality)    | Indica si los dos parámetros son iguales.
[HStringReference::operator!](#operator-inequality)  | Indica si los dos parámetros no son iguales.
[HStringReference::operator&lt;](#operator-less-than) | Indica si el primer parámetro es menor que el segundo parámetro.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HStringReference`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference::CopyTo

Copia el `HStringReference` objeto actual en un objeto HSTRING.

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

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference::Get

Recupera el valor del identificador HSTRING subyacente.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valor devuelto

El valor del identificador HSTRING subyacente.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Recupera un puntero a los datos de cadena subyacentes.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parámetros

*longitud* Puntero a una variable **int** que recibe la longitud de los datos.

### <a name="return-value"></a>Valor devuelto

Un **puntero const** a los datos de cadena subyacentes.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference::HStringReference

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
Un parámetro de plantilla que especifica `HStringReference` el tamaño del búfer de destino.

*Str*<br/>
Una referencia a una cadena de caracteres anchos.

*Len*<br/>
La longitud máxima del búfer de *parámetros str* que se va a utilizar en esta operación. Si no se especifica el parámetro *len,* se utiliza todo el parámetro *str.* Si *len* es mayor que *sizeDest*, *len* se establece en *sizeDest*-1.

*Otro*<br/>
Otro `HStringReference` objeto.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa `HStringReference` un nuevo objeto que tiene el mismo tamaño que el parámetro *str*.

El segundo constructor inicializa `HStringReference` un nuevo objeto que el tamaño specifeid por parámetro *len*.

El tercer constructor inicializa `HStringReference` un nuevo objeto en el valor del *otro* parámetro y, a continuación, destruye el *otro* parámetro.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference::operator ?

Mueve el valor `HStringReference` de otro `HStringReference` objeto al objeto actual.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Objeto `HStringReference` existente.

### <a name="remarks"></a>Observaciones

El valor del *otro* objeto existente se `HStringReference` copia en el objeto actual y, a continuación, se destruye el *otro* objeto.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference::operador ?

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

*Lhs*<br/>
El primer parámetro que se va a comparar. *lhs* puede `HStringReference` ser un objeto o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro que se va a comparar.  *rhs* puede `HStringReference` ser un objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los *parámetros lhs* y *rhs* son iguales; de lo contrario, **false**.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference::operator!

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

*Lhs*<br/>
El primer parámetro que se va a comparar. *lhs* puede `HStringReference` ser un objeto o un identificador HSTRING.

*rhs*<br/>
El segundo parámetro que se va a comparar.  *rhs* puede `HStringReference` ser un objeto o un identificador HSTRING.

### <a name="return-value"></a>Valor devuelto

**true** si los *parámetros lhs* y *rhs* no son iguales; de lo contrario, **false**.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference::operator&lt;

Indica si el primer parámetro es menor que el segundo parámetro.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parámetros

*Lhs*<br/>
El primer parámetro que se va a comparar. *lhs* puede ser una `HStringReference`referencia a un archivo .

*rhs*<br/>
El segundo parámetro que se va a comparar.  *rhs* puede ser una `HStringReference`referencia a un archivo .

### <a name="return-value"></a>Valor devuelto

**true** si el parámetro *lhs* es menor que el parámetro *rhs;* de lo contrario, **false**.
