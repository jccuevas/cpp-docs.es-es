---
title: Clase bad_exception
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 1795a44d2d31cfbad964b41ef03e4bf65b401352
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246205"
---
# <a name="badexception-class"></a>Clase bad_exception

La clase describe una excepción que se puede iniciar desde un controlador inesperado.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_exception : public exception {};

bad_exception();
bad_exception(const bad_exception&);
bad_exception& operator=(const bad_exception&);
const char* what() const override;
```

## <a name="remarks"></a>Comentarios

[unexpected](../standard-library/exception-functions.md#unexpected) inicia `bad_exception` en lugar de terminar o de llamar a otra función especificada con [set_unexpected](../standard-library/exception-functions.md#set_unexpected) si `bad_exception` está incluido en la lista de excepciones de una función.

El valor devuelto por `what` es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.

Para obtener una lista de miembros heredados por la clase `bad_exception`, vea [Exception (Clase)](../standard-library/exception-class.md).

## <a name="example"></a>Ejemplo

Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de [unexpected](../standard-library/exception-functions.md#unexpected) iniciando `bad_exception`.
