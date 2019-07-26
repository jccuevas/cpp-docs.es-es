---
title: Clase bad_array_new_length
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: b00042513364ac04b62ac7e1943d912dcb78f212
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459489"
---
# <a name="badarraynewlength-class"></a>Clase bad_array_new_length

La clase describe una excepción que se inicia para indicar que una solicitud de asignación no se realizó correctamente debido a que el tamaño de la matriz es menor que cero o mayor que el límite.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_array_new_length : public bad_alloc {
    public: bad_array_new_length() noexcept;
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Comentarios

El valor devuelto `what` por es una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<new>

## <a name="see-also"></a>Vea también

[Exception (clase)](../standard-library/exception-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
