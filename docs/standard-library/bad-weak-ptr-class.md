---
title: bad_weak_ptr (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::bad_weak_ptr
dev_langs:
- C++
helpviewer_keywords:
- bad_weak_ptr
- bad_weak_ptr class
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cb6e00341e5e40d04be1d447f03e43818e53291
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839837"
---
# <a name="badweakptr-class"></a>bad_weak_ptr (Clase)

Informa de una excepción weak_ptr errónea.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_weak_ptr : public std::exception
 {
public:
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

## <a name="requirements"></a>Requisitos

**Encabezado:** \<memory>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[weak_ptr (Clase)](../standard-library/weak-ptr-class.md)<br/>
