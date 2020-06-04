---
title: Constructores de copia y operadores de asignación de copia (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- = operator [C++], copying objects
- assignment statements [C++], copying objects
- assignment operators [C++], for copying objects
- objects [C++], copying
- initializing objects, by copying objects
- copying objects
- assigning values to copy objects
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
ms.openlocfilehash: beabe4c6219975d33c7af98a94498188c9abfa55
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189538"
---
# <a name="copy-constructors-and-copy-assignment-operators-c"></a>Constructores de copia y operadores de asignación de copia (C++)

> [!NOTE]
> A partir de C++ 11, se admiten dos tipos de asignación en el idioma: *asignación de copia* y *asignación de movimiento*. En este artículo, "asignación" significa asignación de copia a menos que se establezca explícitamente lo contrario. Para obtener información sobre la asignación de movimiento, vea [constructores de movimiento yC++operadores de asignación de movimiento ()](move-constructors-and-move-assignment-operators-cpp.md).
>
> Tanto la operación de asignación como la operación de inicialización provocan que los objetos se copien.

- **Asignación**: cuando el valor de un objeto se asigna a otro objeto, el primer objeto se copia en el segundo objeto. Por lo tanto,

    ```cpp
    Point a, b;
    ...
    a = b;
    ```

   hace que el valor de `b` se copie en `a`.

- **Inicialización**: la inicialización se produce cuando se declara un nuevo objeto, cuando los argumentos se pasan a funciones por valor o cuando los valores se devuelven de las funciones por valor.

Puede definir la semántica de “copy” para los objetos de tipo de clase. Por ejemplo, considere este código:

```cpp
TextFile a, b;
a.Open( "FILE1.DAT" );
b.Open( "FILE2.DAT" );
b = a;
```

El código anterior podría significar “copiar el contenido de FILE1.DAT en FILE2.DAT” o podría significar “omitir FILE2.DAT y convertir `b` en un segundo identificador para FILE1.DAT”. Debe asociar la semántica de copia correspondiente a cada clase, de la manera siguiente.

- Mediante el operador de asignación **Operator =** junto con una referencia al tipo de clase como el tipo de valor devuelto y el parámetro que se pasa por referencia **const** , por ejemplo `ClassName& operator=(const ClassName& x);`.

- Utilizando el constructor de copias.

Si no declara un constructor de copias, el compilador genera uno automáticamente miembro a miembro.  Si no declara una asignación de copia, el compilador genera una automáticamente miembro a miembro. Declarar un constructor de copias no suprime el operador de asignación de copias generado por el compilador, ni viceversa. Si se implementa cualquiera de ellos, es recomendable implementar también el otro de modo que el significado del código esté claro.

El constructor de copias toma un argumento de tipo <em>Class-name</em> <strong>&</strong>, donde *Class-Name* es el nombre de la clase para la que se define el constructor. Por ejemplo:

```cpp
// spec1_copying_class_objects.cpp
class Window
{
public:
    Window( const Window& ); // Declare copy constructor.
    // ...
};

int main()
{
}
```

> [!NOTE]
> Haga que el tipo del argumento del constructor de copia **const const** <em>class-name</em> <strong>&</strong> siempre que sea posible. Esto evita que el constructor de copias modifique accidentalmente el objeto del que se está copiando. También permite copiar desde objetos **const** .

## <a name="compiler-generated-copy-constructors"></a>Constructores de copias generados por el compilador

Los constructores de copias generados por el compilador, como los constructores de copias definidos por el usuario, tienen un único argumento de tipo "referencia a *Class-Name*". Una excepción es cuando todas las clases base y las clases de miembro tienen constructores de copias declarados que toman un único argumento de tipo **const** <em>class-name</em> <strong>&</strong>. En tal caso, el argumento del constructor de copias generado por el compilador también es **const**.

Cuando el tipo de argumento para el constructor de copias no es **const**, la inicialización mediante la copia de un objeto **const** genera un error. Lo contrario no es cierto: Si el argumento es **const**, puede inicializar mediante la copia de un objeto que no es **const**.

Los operadores de asignación generados por el compilador siguen el mismo patrón con respecto a **const.** Toman un solo argumento de tipo <em>Class-name</em> <strong>&</strong> a menos que los operadores de asignación de todas las clases base y miembro tomen argumentos de tipo **const** <em>Class-Name</em> <strong>&</strong>. En este caso, el operador de asignación generado de la clase toma un argumento **const** .

> [!NOTE]
> Cuando los constructores de copias, generados por el compilador o definidos por el usuario, inicializan las clases base virtuales, estas se inicializan solo una vez: en el momento en que se construyen.

Las implicaciones son similares a las del constructor de copias. Cuando el tipo de argumento no es **const**, la asignación de un objeto **const** genera un error. Lo contrario no es cierto: si se asigna un valor **const** a un valor que no es **const**, la asignación se realiza correctamente.

Para obtener más información sobre los operadores de asignación sobrecargados, vea [asignación](../cpp/assignment.md).
