---
title: Clase add_lvalue_reference
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_lvalue_reference
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
ms.openlocfilehash: 5f822e3393853c780bfe4ee86d5a5c799ec7646d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617672"
---
# <a name="add_lvalue_reference-class"></a>Clase add_lvalue_reference

Convierte una referencia en un tipo a partir de un tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct add_lvalue_reference;

template <class T>
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Observaciones

Una instancia del modificador de tipo contiene un tipo modificado que es *t* si *t* es una referencia lvalue; de lo contrario, `T&` .

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

using namespace std;
int main()
{
    int val = 0;
    add_lvalue_reference_t<int> p = (int&)val;
    p = p;  // to quiet "unused" warning
    cout << "add_lvalue_reference_t<int> == "
        << typeid(p).name() << endl;

    return (0);
}
```

```Output
add_lvalue_reference_t<int> == int
```

## <a name="requirements"></a>Requisitos

**Encabezado:**\<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](type-traits.md)\
[remove_reference (clase)](remove-reference-class.md)
