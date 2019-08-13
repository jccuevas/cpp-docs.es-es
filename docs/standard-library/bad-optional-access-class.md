---
title: Clase bad_optional_access
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: 043b0360c7e0be48267c8f406dbfea50eeb5a8e3
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957099"
---
# <a name="bad_optional_access-class"></a>Clase bad_optional_access

Define el tipo de objetos que se inician como excepciones para notificar la situación en la que se realiza un intento `optional` de obtener acceso al valor de un objeto que no contiene un valor.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>Vea también

[\<> opcional](optional.md)\
[clase opcional](optional-class.md)
