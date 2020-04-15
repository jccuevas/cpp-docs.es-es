---
title: creación de instancias explícita
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361960"
---
# <a name="explicit-instantiation"></a>creación de instancias explícita

Puede utilizar la creación de instancias explícita para crear una instancia de una clase o una función con plantilla sin usarla realmente en el código. Como esto es útil cuando se crean archivos de biblioteca (.lib) que utilizan plantillas para la distribución, las definiciones de plantillas sin instancias no se colocan en archivos objeto (.obj).

Este código crea `MyStack` explícitamente una instancia para variables **int** y seis elementos:

```cpp
template class MyStack<int, 6>;
```

Esta instrucción crea una instancia de `MyStack` sin reservar ningún almacenamiento para un objeto. Se genera el código para todos los miembros.

La línea siguiente crea explícitamente instancias solo de la función miembro de constructor:

```cpp
template MyStack<int, 6>::MyStack( void );
```

Puede crear instancias explícitas de plantillas de función mediante un argumento de tipo específico para volver a declararlas, como se muestra en el ejemplo de Creación de instancias de plantilla de [función](../cpp/function-template-instantiation.md).

Puede utilizar la palabra clave **extern** para evitar la creación automática de instancias de miembros. Por ejemplo:

```cpp
extern template class MyStack<int, 6>;
```

Del mismo modo, puede marcar determinados miembros como externos y no crear instancias de ellos:

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

Puede usar la palabra clave **extern** para evitar que el compilador genere el mismo código de creación de instancias en más de un módulo de objetos. Para crear instancias de la función de plantilla se deben utilizar los parámetros de plantilla explícitos especificados en al menos un módulo vinculado si se llama a la función; de lo contrario, se producirá un error del vinculador cuando se compile el programa.

> [!NOTE]
> La palabra clave **extern** de la especialización solo se aplica a las funciones miembro definidas fuera del cuerpo de la clase. Las funciones definidas dentro de la declaración de clase se consideran funciones insertadas y siempre se crean instancias de ellas.

## <a name="see-also"></a>Consulte también

[Plantillas de función](../cpp/function-templates.md)
