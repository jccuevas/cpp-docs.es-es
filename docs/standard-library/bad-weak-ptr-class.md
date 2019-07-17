---
title: bad_weak_ptr (Clase)
ms.date: 11/04/2016
f1_keywords:
- memory/std::bad_weak_ptr
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
ms.openlocfilehash: 8ea29f12a8a86bd6b58c5051645182d69ff43389
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246183"
---
# <a name="badweakptr-class"></a>bad_weak_ptr (Clase)

Informa de una excepción weak_ptr errónea.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_weak_ptr : public std::exception
{
    bad_weak_ptr();
    const char *what() throw();
};
```

## <a name="remarks"></a>Comentarios

La clase describe una excepción que se puede iniciar desde el constructor [shared_ptr (Clase)](../standard-library/shared-ptr-class.md) que toma un argumento de tipo [weak_ptr (Clase)](../standard-library/weak-ptr-class.md). La función miembro `what` devuelve `"bad_weak_ptr"`.

## <a name="example"></a>Ejemplo

```cpp
// std__memory__bad_weak_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int);
        wp = sp;
    }

    try
    {
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired
    }
    catch (const std::bad_weak_ptr&)
    {
        std::cout << "bad weak pointer" << std::endl;
    }
    catch (...)
    {
        std::cout << "unknown exception" << std::endl;
    }

    return (0);
}
```

```Output
bad weak pointer
```

## <a name="see-also"></a>Vea también

[weak_ptr (Clase)](../standard-library/weak-ptr-class.md)<br/>
