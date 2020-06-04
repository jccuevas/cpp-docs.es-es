---
title: Acceso a miembros
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179424"
---
# <a name="member-access"></a>Acceso a miembros

El acceso a miembros de clase se puede controlar sobrecargando el operador de acceso a miembros ( **->** ). Este operador se considera un operador unario en este uso, y la función de operador sobrecargado debe ser una función miembro de clase. Por lo tanto, la declaración de una función de ese tipo es:

## <a name="syntax"></a>Sintaxis

```
class-type *operator->()
```

## <a name="remarks"></a>Observaciones

donde *class-type* es el nombre de la clase a la que pertenece este operador. La función de operador de acceso a miembros debe ser una función miembro no estática.

Este operador se usa (a menudo junto con el operador de desreferenciación de puntero) para implementar "punteros inteligentes" que validan punteros antes del uso de desreferenciación o de recuento.

El elemento de lenguaje **.** no se puede sobrecargar el operador de acceso a miembros.

## <a name="see-also"></a>Consulte también

[Sobrecarga de operadores](../cpp/operator-overloading.md)
