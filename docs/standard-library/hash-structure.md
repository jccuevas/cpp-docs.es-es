---
title: hash (Estructura)
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::hash
ms.assetid: e5a41202-ef3b-45d0-b3a7-4c2dbdc0487a
ms.openlocfilehash: ba05d70692b2f85c1a14f319fb1e92dcadc0ccce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158786"
---
# <a name="hash-structure"></a>hash (Estructura)

La clase de plantilla define su método para que devuelva `val.hash_code()`. El método define una función hash que se usa para asignar valores de tipo [type_index](../standard-library/type-index-class.md) a una distribución de valores de índice.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct hash<type_index>
: public unary_function<type_index, size_t>
{ // hashes a typeinfo object
    size_t operator()(type_index val) const;

};
```

## <a name="see-also"></a>Vea también

[\<typeindex>](../standard-library/typeindex.md)<br/>
