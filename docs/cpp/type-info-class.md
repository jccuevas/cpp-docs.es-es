---
title: type_info (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 7a016fe8fee4e5765e6172184bfa9c90eecbc687
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160676"
---
# <a name="type_info-class"></a>type_info (Clase)

En la clase **type_info** se describe la información de tipo generada en el programa por el compilador. Los objetos de esta clase almacenan de forma eficaz un puntero a un nombre para el tipo. La clase **type_info** también almacena un valor codificado adecuado para comparar dos tipos de igualdad o de ordenación. Las reglas de codificación y la secuencia de intercalación para tipos no se especifican y pueden diferir entre programas.

Se debe incluir el archivo de encabezado `<typeinfo>` para poder utilizar la clase **type_info** . La interfaz para la clase **type_info** es:

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

No se pueden crear instancias de objetos de la clase **type_info** directamente, porque la clase solo tiene un constructor de copias privado. La única manera de construir un objeto de **type_info** (temporal) es usar el operador [typeid](../cpp/typeid-operator.md) . Dado que el operador de asignación también es privado, no puede copiar o asignar objetos de la clase **type_info**.

`type_info::hash_code` define una función hash adecuada para asignar valores de tipo **TypeInfo** a una distribución de valores de índice.

Los operadores `==` y `!=` se pueden utilizar para comparar la igualdad y la desigualdad con otros objetos **type_info** , respectivamente.

No hay ningún vínculo entre el orden de intercalación de tipos y las relaciones de herencia. Utilice la función miembro `type_info::before` para determinar la secuencia de intercalación de los tipos. No hay ninguna garantía de que `type_info::before` producirá el mismo resultado en programas distintos o incluso en diferentes ejecuciones del mismo programa. De esta manera, `type_info::before` es similar al operador Address-of `(&)`.

La función miembro `type_info::name` devuelve un `const char*` a una cadena terminada en null que representa el nombre legible del tipo. La memoria a la que se señala se almacena en caché y nunca debe desasignarse directamente.

La función miembro `type_info::raw_name` devuelve un `const char*` a una cadena terminada en null que representa el nombre representativo del tipo de objeto. El nombre se almacena realmente en forma representativa para ahorrar espacio. Por consiguiente, esta función es más rápida que la `type_info::name` porque no es necesario quitar el nombre del nombre. La cadena devuelta por la función `type_info::raw_name` es útil en las operaciones de comparación pero no es legible. Si necesita una cadena inteligible para el usuario, utilice en su lugar la función `type_info::name`.

La información de tipo se genera para las clases polimórficas solo si se especifica la opción del compilador [/gr (habilitar información de tipo en tiempo de ejecución)](../build/reference/gr-enable-run-time-type-information.md) .

## <a name="see-also"></a>Consulte también

[Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)
