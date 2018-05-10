---
title: bad_exception (Clase)| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41b30763f1382b7a12f68cd6a45b87960f623649
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="badexception-class"></a>Clase bad_exception

La clase describe una excepción que se puede iniciar desde un controlador inesperado.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>Comentarios

[unexpected](../standard-library/exception-functions.md#unexpected) inicia `bad_exception` en lugar de terminar o de llamar a otra función especificada con [set_unexpected](../standard-library/exception-functions.md#set_unexpected) si `bad_exception` está incluido en la lista de excepciones de una función.

El valor que devuelve **what** es una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.

Para obtener una lista de miembros heredados por la clase `bad_exception`, vea [Exception (Clase)](../standard-library/exception-class.md).

## <a name="example"></a>Ejemplo

Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de [unexpected](../standard-library/exception-functions.md#unexpected) iniciando `bad_exception`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exception>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[exception (Clase)](../standard-library/exception-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
