---
title: Clase bad_array_new_length
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 823da1555119735e9aa1c46aa4db2e3a47affdec
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268697"
---
# <a name="badarraynewlength-class"></a>Clase bad_array_new_length

La clase describe una excepción iniciada para indicar que una solicitud de asignación no se realizó correctamente debido al tamaño de la matriz, menor que cero o mayor que su límite.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por `what` es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<new>

## <a name="see-also"></a>Vea también

[exception (Clase)](../standard-library/exception-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
