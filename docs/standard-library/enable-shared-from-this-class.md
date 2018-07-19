---
title: enable_shared_from_this (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46e5b0b0c55c5a5dd0a48d2437fc83fa43226f5a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956150"
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this (Clase)

Ayuda a generar un `shared_ptr`.

## <a name="syntax"></a>Sintaxis

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>Parámetros

*Ty* tipo controlado por el puntero compartido.

## <a name="remarks"></a>Comentarios

Los objetos derivados de `enable_shared_from_this` pueden usar los métodos `shared_from_this` en las funciones miembro para crear propietarios [shared_ptr](../standard-library/shared-ptr-class.md) de la instancia que comparte propiedad con propietarios `shared_ptr` existentes. En caso contrario, si crea un nuevo `shared_ptr` utilizando **esto**, es distinto de existente `shared_ptr` los propietarios, que pueden provocar referencias no válidas o que el objeto se elimine más de una vez.

Los constructores, el destructor y el operador de asignación están protegidos para evitar un uso incorrecto accidental. El tipo de argumento de plantilla *Ty* debe ser del tipo de la clase derivada.

Para obtener un ejemplo de uso, vea [enable_shared_from_this::shared_from_this](#shared_from_this).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<memory>

**Espacio de nombres:** std

## <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this

Genera un `shared_ptr` que comparte la propiedad de la instancia con propietarios `shared_ptr` existentes.

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Comentarios

Al derivar objetos desde la clase base `enable_shared_from_this`, las funciones miembro de plantilla `shared_from_this` devuelven un objeto [shared_ptr (Clase)](../standard-library/shared-ptr-class.md) que comparte la propiedad de esta instancia con propietarios `shared_ptr` existentes. En caso contrario, si crea un nuevo `shared_ptr` desde **esto**, es distinto de existente `shared_ptr` los propietarios, que pueden provocar referencias no válidas o que el objeto se elimine más de una vez. El comportamiento es indefinido si se llama a `shared_from_this` en una instancia que ya no pertenece a un objeto `shared_ptr`.

### <a name="example"></a>Ejemplo

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="see-also"></a>Vea también

[enable_shared_from_this:: shared_from_this](#shared_from_this)<br/>
[shared_ptr (Clase)](../standard-library/shared-ptr-class.md)<br/>