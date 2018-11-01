---
title: Clase bad_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 94d1104b66fc6bd84e209caa23ce309cffd9fa85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457465"
---
# <a name="badexception-class"></a>Clase bad_exception

La clase describe una excepción que se puede iniciar desde un controlador inesperado.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Comentarios

[unexpected](../standard-library/exception-functions.md#unexpected) inicia `bad_exception` en lugar de terminar o de llamar a otra función especificada con [set_unexpected](../standard-library/exception-functions.md#set_unexpected) si `bad_exception` está incluido en la lista de excepciones de una función.

El valor devuelto por `what` es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.

Para obtener una lista de miembros heredados por la clase `bad_exception`, vea [Exception (Clase)](../standard-library/exception-class.md).

## <a name="example"></a>Ejemplo

Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de [unexpected](../standard-library/exception-functions.md#unexpected) iniciando `bad_exception`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exception>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[exception (Clase)](../standard-library/exception-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
