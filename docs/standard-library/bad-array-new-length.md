---
title: bad_array_new_length (clase)
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_array_new_length
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: c4f4f58f7b28960bbacf695a675fbe4f20a54192
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443703"
---
# <a name="bad_array_new_length-class"></a>bad_array_new_length (clase)

La clase describe una excepción que se inicia para indicar que una solicitud de asignación no se realizó correctamente debido a que el tamaño de la matriz es menor que cero o mayor que el límite.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Observaciones

El valor devuelto por `what` es una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<nuevo >

## <a name="see-also"></a>Consulte también

\ de [clase de excepción](../standard-library/exception-class.md)
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
