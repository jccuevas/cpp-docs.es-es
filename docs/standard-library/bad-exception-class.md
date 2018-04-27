---
title: bad_exception (Clase)| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- exception/std::bad_exception
dev_langs:
- C++
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b1b332b4f76f24f873fd8a57d302fc2643a71f1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
