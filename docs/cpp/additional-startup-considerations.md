---
title: Consideraciones de inicio adicionales | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d629451161d94853558887eb7029fc165d13d9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079224"
---
# <a name="additional-startup-considerations"></a>Consideraciones de inicio adicionales

En C++, la creación y destrucción de objetos pueden implicar la ejecución de código de usuario. Por lo tanto, es importante entender qué inicializaciones se producen antes de la entrada a `main` y qué destructores se invocan después de salir de `main`. (Para obtener información detallada sobre la construcción y destrucción de objetos, consulte [constructores](../cpp/constructors-cpp.md) y [destructores](../cpp/destructors-cpp.md).)

Las inicializaciones siguientes tienen lugar antes de la entrada a `main`:

- Inicialización predeterminada de datos estáticos en cero. Todos los datos estáticos sin inicializadores explícitos se establecen en cero antes de ejecutar cualquier otro código, incluida la inicialización en tiempo de ejecución. Los miembros de datos estáticos todavía se deben definir explícitamente.

- Inicialización de objetos estáticos globales en una unidad de traducción. Esto puede darse antes de la entrada a `main` o antes del primer uso de cualquier función u objeto de unidad de traducción del objeto.

**Específicos de Microsoft**

En Microsoft C++, objetos estáticos globales se inicializan antes de la entrada a `main`.

**FIN de Específicos de Microsoft**

Los objetos estáticos globales que son mutuamente interdependientes pero en diferentes unidades de traducción pueden provocar un comportamiento incorrecto.

## <a name="see-also"></a>Vea también

[Inicio y finalización](../cpp/startup-and-termination-cpp.md)