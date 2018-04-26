---
title: type_index (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86058cd8deb0ddd9458c8882bb31029d365cb110
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
