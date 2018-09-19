---
title: Creación de instancias explícita | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85ea920dc01f408c7723fb082e6a0e60fa9a00e8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110671"
---
# <a name="explicit-instantiation"></a>creación de instancias explícita

Puede utilizar la creación de instancias explícita para crear una instancia de una clase o una función con plantilla sin usarla realmente en el código. Como esto es útil cuando se crean archivos de biblioteca (.lib) que utilizan plantillas para la distribución, las definiciones de plantillas sin instancias no se colocan en archivos objeto (.obj).

Este código crea explícitamente instancias `MyStack` para **int** variables y seis elementos:

```cpp
template class MyStack<int, 6>;
```

Esta instrucción crea una instancia de `MyStack` sin reservar ningún almacenamiento para un objeto. Se genera el código para todos los miembros.

La línea siguiente crea explícitamente instancias solo de la función miembro de constructor:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Se pueden crear explícitamente instancias de plantillas de función mediante un argumento de tipo específico para volver a declararlas, como se muestra en el ejemplo de [crear instancias de plantillas de función](../cpp/function-template-instantiation.md).

Puede usar el **extern** palabra clave para evitar la creación automática de instancias de miembros. Por ejemplo:

```cpp
extern template class MyStack<int, 6>;
```

Del mismo modo, puede marcar determinados miembros como externos y no crear instancias de ellos:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Puede usar el **extern** palabra clave para impedir que el compilador genera el mismo código de creación de instancias en más de un módulo de objeto. Para crear instancias de la función de plantilla se deben utilizar los parámetros de plantilla explícitos especificados en al menos un módulo vinculado si se llama a la función; de lo contrario, se producirá un error del vinculador cuando se compile el programa.

> [!NOTE]
>  El **extern** palabra clave en la especialización solo se aplica a las funciones miembro definidas fuera del cuerpo de la clase. Las funciones definidas dentro de la declaración de clase se consideran funciones insertadas y siempre se crean instancias de ellas.

## <a name="see-also"></a>Vea también

[Plantillas de función](../cpp/function-templates.md)