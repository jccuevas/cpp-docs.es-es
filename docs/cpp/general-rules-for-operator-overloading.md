---
title: Reglas generales para la sobrecarga de operadores
ms.date: 11/04/2016
helpviewer_keywords:
- operator overloading [C++], rules
ms.assetid: eb2b3754-35f7-4832-b1da-c502893dc0c7
ms.openlocfilehash: 0c8cbea3411acd50be376ae0853a143af57458f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188612"
---
# <a name="general-rules-for-operator-overloading"></a>Reglas generales para la sobrecarga de operadores

Las reglas siguientes restringen la forma en que se implementan los operadores sobrecargados. Sin embargo, no se aplican a los operadores [New](../cpp/new-operator-cpp.md) y [Delete](../cpp/delete-operator-cpp.md) , que se describen por separado.

- No se pueden definir nuevos operadores, como **.** .

- No se puede volver a definir el significado de los operadores cuando se aplican a los tipos de datos integrados.

- Los operadores sobrecargados deben ser una función miembro de clase no estática o una función global. Una función global que necesita acceso a miembros de clase privados o protegidos se debe declarar como friend de esa clase. Una función global debe tomar al menos un argumento que sea de clase o de tipo enumerado, o que sea una referencia a una clase o a un tipo enumerado. Por ejemplo:

    ```cpp
    // rules_for_operator_overloading.cpp
    class Point
    {
    public:
        Point operator<( Point & );  // Declare a member operator
                                     //  overload.
        // Declare addition operators.
        friend Point operator+( Point&, int );
        friend Point operator+( int, Point& );
    };

    int main()
    {
    }
    ```

   En el ejemplo de código anterior se declara el operador "menos que" como función miembro; sin embargo, los operadores de suma se declaran como funciones globales con acceso de confianza. Observe que se puede proporcionar más de una implementación para un operador determinado. En el caso del operador de suma anterior, las dos implementaciones se proporcionan para facilitar la propiedad conmutativa. Es tan probable que se implementen los operadores que agregan un `Point` a un `Point`, **int** a un `Point`, etc.

- Los operadores obedecen a la prioridad, la agrupación y el número de operandos dictados por su uso típico con los tipos integrados. Por lo tanto, no hay ninguna manera de expresar el concepto "agregar 2 y 3 a un objeto de tipo `Point`", se espera que 2 se agregue a la coordenada *x* y 3 para que se agregue a la coordenada *y* .

- Los operadores unarios declarados como funciones miembro no toman ningún argumento; si se declaran como funciones globales, toman un argumento.

- Los operadores binarios declarados como funciones miembro toman un argumento; si se declaran como funciones globales, toman dos argumentos.

- Si se puede usar un operador como operador unario o binario ( __&__ , __*__ , __+__ y __-__ ), puede sobrecargar cada uso por separado.

- Los operadores sobrecargados no pueden tener argumentos predeterminados.

- Todas las clases derivadas heredan todos los operadores sobrecargados excepto la asignación (**operador =** ).

- El primer argumento para los operadores sobrecargados de función miembro siempre es del tipo de clase del objeto para el que se invoca el operador (la clase en la que se declara el operador o una clase derivada de ella). No se proporciona ninguna conversión para el primer argumento.

Observe que el significado de cualquiera de los operadores se puede cambiar por completo. Esto incluye el significado de los operadores Address-of ( **&** ), assignment ( **=** ) y Call-Call. Además, las identidades en las que se puede confiar para los tipos integrados pueden cambiarse mediante la sobrecarga de operadores. Por ejemplo, las cuatro instrucciones siguientes suelen ser equivalentes cuando se evalúan completamente:

```cpp
var = var + 1;
var += 1;
var++;
++var;
```

No se puede confiar en esta identidad para los tipos de clase que sobrecargan operadores. Además, algunos requisitos implícitos en el uso de estos operadores para los tipos básicos se relajan para los operadores sobrecargados. Por ejemplo, el operador de suma/asignación, **+=** , requiere que el operando izquierdo sea un valor l cuando se aplica a los tipos básicos; no existe este requisito cuando el operador está sobrecargado.

> [!NOTE]
> Por coherencia, a menudo es mejor seguir el modelo de los tipos integrados al definir operadores sobrecargados. Si la semántica de un operador sobrecargado difiere mucho de su significado en otros contextos, puede ser más confusa que útil.

## <a name="see-also"></a>Consulte también

[Sobrecarga de operadores](../cpp/operator-overloading.md)
