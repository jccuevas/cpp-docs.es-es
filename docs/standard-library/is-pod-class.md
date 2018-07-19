---
title: Clase is_pod | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c655ea4adec0364f35d0b43c637eae9c270cdb0e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962070"
---
# <a name="ispod-class"></a>is_pod (Clase)

Comprueba si el tipo es POD.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parámetros

*T* el tipo de consulta.

## <a name="remarks"></a>Comentarios

`is_pod<T>::value` es **true** si el tipo *T* es datos antiguos sin formato (POD). De lo contrario es **false**.

Los tipos aritméticos, tipos de enumeración, tipos de puntero y el puntero a tipos de miembro son POD.

Una versión cv completa de un tipo POD es en sí misma un tipo POD.

Una matriz de POD es en sí misma POD.

Una estructura o unión cuyos miembros de datos no estáticos son todos POD, es en sí misma POD si reúne estas condiciones:

- No hay ningún constructor declarado por el usuario.

- No hay ningún miembro de datos no estáticos privado o protegido.

- Ninguna clase base.

- No hay funciones virtuales.

- No hay ningún miembro de datos no estáticos de tipo de referencia.

- No hay ningún operador de asignación de copia definido por el usuario.

- No hay ningún destructor definido por el usuario.

Por lo tanto, puede compilar recursivamente estructuras y matrices POD que contienen estructuras y matrices POD.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
