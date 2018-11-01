---
title: messages_base (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: 750c9f36ce7f96a065e0e29111ea379a48595328
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611619"
---
# <a name="messagesbase-class"></a>messages_base (Clase)

La clase base describe un **int** tipo para el catálogo de mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>Comentarios

El catálogo de tipos es un sinónimo de tipo **int** que describe los posibles valores devueltos de messages:: [do_open](../standard-library/messages-class.md#do_open).

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
