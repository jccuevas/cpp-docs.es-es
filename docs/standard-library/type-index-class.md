---
title: type_index (Clase)
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 8807a041ab1c6ef47a9c3c12dac2688f121f6cfa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650497"
---
# <a name="typeindex-class"></a>type_index (Clase)

La clase `type_index` contiene un puntero a [type_info (Clase)](../cpp/type-info-class.md) para facilitar la indización de estos objetos.

class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };

El constructor inicializa `ptr` en `&tinfo`.

`name` devuelve `ptr->name()`.

`hash_code` devuelve `ptr->hash_code().`

`operator==` devuelve `*ptr == right.ptr`.

`operator!=` devuelve `!(*this == right)`.

`operator<` devuelve `*ptr->before(*right.ptr)`.

`operator<=` devuelve `!(right < *this).`

`operator>` devuelve `right < *this`.

`operator>=` devuelve `!(*this < right)`.

## <a name="see-also"></a>Vea también

[Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)<br/>
[\<typeindex>](../standard-library/typeindex.md)<br/>
