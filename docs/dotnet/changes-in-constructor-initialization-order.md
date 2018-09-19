---
title: Los cambios en el orden de inicialización de constructores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd54e9810131f3ddfabe458c70ddef081568a9cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397694"
---
# <a name="changes-in-constructor-initialization-order"></a>Cambios en el orden de inicialización de constructores

El orden de inicialización para los constructores de clase ha cambiado de extensiones administradas para C++ a Visual C++.

## <a name="comparison-of-constructor-initialization-order"></a>Comparación de orden de inicialización de constructores

En extensiones administradas para C++, la inicialización del constructor se produjo en el orden siguiente:

1. El constructor de la clase base, si existe, se invoca.

1. Se evalúa la lista de inicialización de la clase.

1. Se ejecuta el cuerpo de código del constructor de clase.

Este orden de ejecución sigue las mismas convenciones que en la programación de C++ nativa. El nuevo lenguaje de Visual C++ prescribe el siguiente orden de ejecución para las clases CLR:

1. Se evalúa la lista de inicialización de la clase.

1. El constructor de la clase base, si existe, se invoca.

1. Se ejecuta el cuerpo de código del constructor de clase.

Tenga en cuenta que este cambio se aplica únicamente a las clases CLR; las clases nativas de Visual C++ puede seguir las convenciones anteriores. En ambos casos, estas reglas en cascada hacia arriba en toda la cadena de toda la jerarquía de una clase determinada.

Tenga en cuenta el siguiente ejemplo de código mediante extensiones administradas para C++:

```
__gc class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

__gc class B : public A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

Siguiendo el orden de inicialización del constructor prescrito por encima, deberíamos ver el siguiente orden de ejecución cuando nuevas instancias de clase `B` se construyen:

1. El constructor de la clase base `A` se invoca. El `_n` miembro se inicializa en `1`.

1. La lista de inicialización para la clase `B` se evalúa. El `_m` miembro se inicializa en `1`.

1. El cuerpo de código de clase `B` se ejecuta.

Ahora, considere el mismo código en la nueva sintaxis de Visual C++:

```
ref class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

ref class B : A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

El orden de ejecución cuando nuevas instancias de clase `B` se construyen en la nueva sintaxis es:

1. La lista de inicialización para la clase `B` se evalúa. El `_m` miembro se inicializa en `0` (`0` es el valor inicializado de los `_m` miembro de clase).

1. El constructor de la clase base `A` se invoca. El `_n` miembro se inicializa en `1`.

1. El cuerpo de código de clase `B` se ejecuta.

Tenga en cuenta que una sintaxis similar produce resultados diferentes para estos ejemplos de código. El constructor de clase `B` depende del valor de la clase base `A` para inicializar su miembro. Sin embargo, el constructor de clase `A` no se ha invocado todavía. Esta dependencia puede ser especialmente peligrosa cuando la clase heredada depende de una asignación de memoria o recursos que se produzca en el constructor de clase base.

## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>Qué significa pasar de extensiones administradas para C++ a Visual C++ 2010

En muchos casos, los cambios en el orden de ejecución de los constructores de clase deben ser transparentes para el programador porque las clases base no tienen ninguna noción del comportamiento de las clases heredadas. Sin embargo, como se muestran en estos ejemplos de código, los constructores de clases heredadas pueden verse afectados de considerablemente cuando sus listas de inicialización dependen de los valores de miembros de clase base. Al mover el código de extensiones administradas para C++ a la nueva sintaxis, considere la posibilidad de trasladar estas construcciones para el cuerpo del constructor de clase, donde se garantiza que la ejecución se producen por última vez.

## <a name="see-also"></a>Vea también

[Tipos administrados (C++ / c++ / CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Constructores](../cpp/constructors-cpp.md)
