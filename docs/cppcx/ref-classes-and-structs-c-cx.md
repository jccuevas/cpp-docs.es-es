---
title: Ref (Clases y structs) (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3d736b82-0bf0-48cf-bac1-cc9d110b70d1
ms.openlocfilehash: b58c5b64d8f4a60b418fdd2b11318055a8fb618e
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740894"
---
# <a name="ref-classes-and-structs-ccx"></a>Ref (Clases y structs) (C++/CX)

C++/CX admite *clases Ref* y *Structs Ref*definidos por el usuario, así como clases de *valores* y *Structs*de valor definidos por el usuario. Estas estructuras de datos son los contenedores principales por C++los que/CX admite el sistema de tipos Windows Runtime. Su contenido se emite a los metadatos de acuerdo con ciertas reglas específicas y esto permite que se pasen entre Windows Runtime componentes y Plataforma universal de Windows aplicaciones escritas C++ en u otros lenguajes.

Una clase ref o un struct ref tienen estas características esenciales:

- Debe declararse dentro de un espacio de nombres, en el ámbito de espacio de nombres, y en ese espacio de nombres puede tener accesibilidad pública o privada. Únicamente los tipos públicos se emiten para metadatos. No se permiten definiciones de clase pública anidada, incluidas las clases de [enumeración](../cppcx/enums-c-cx.md) públicas anidadas. Para más información, vea [espacios de nombres y visibilidad de tipos](../cppcx/namespaces-and-type-visibility-c-cx.md).

- Puede contener como miembros C++/CX, incluidas clases Ref, clases de valor, Structs de referencia, Structs de valor o Structs de valores que aceptan valores NULL. También puede contener tipos escalares como float64, bool, etc. También puede contener tipos de C++ estándar como `std::vector` o una clase personalizada, mientras no sean públicos. C++Las construcciones/CX pueden tener `public`accesibilidad `protected`, `internal`, `private`, o `protected private` . Todos los miembros `public` o `protected` se emiten para metadatos. Los tipos de C++ estándar deben tener accesibilidad `private`, `internal`o `protected private` , lo que evita que se emitan para metadatos.

- Puede implementar una o más *clases de interfaz* o *structs de interfaz*.

- Puede heredar de una clase base, y las propias clases base tienen restricciones adicionales. La herencia en jerarquías de clases ref públicas tienen más restricciones que la herencia en clases ref privadas.

- Puede no declararse como genérica. Si posee accesibilidad privada, puede ser una plantilla.

- Su vigencia la administra el recuento de referencias automático.

## <a name="declaration"></a>Declaración

El fragmento de código siguiente declara la clase ref `Person` . Tenga en cuenta que C++ `std::map` el tipo estándar se usa en los miembros privados y la`IMapView` interfaz de Windows Runtime se usa en la interfaz pública. Observe también que el operador “^” se anexa a las declaraciones de tipos de referencia.

[!code-cpp[cx_classes#03](../cppcx/codesnippet/CPP/classesstructs/class1.h#03)]

## <a name="implementation"></a>Implementación

En este ejemplo de código se muestra una implementación de la clase ref `Person` .

[!code-cpp[cx_classes#04](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#04)]

## <a name="usage"></a>Uso

En el ejemplo de código siguiente se muestra cómo el código de cliente utiliza la clase ref `Person` .

[!code-cpp[cx_classes#05](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#05)]

También puedes usar semántica de pila para declarar una variable de clase ref local. Este tipo de objeto se comporta como una variable basada en la pila aunque la memoria todavía se asigna dinámicamente. Una diferencia importante es que no puedes asignar una referencia de seguimiento (%) a una variable que se declare utilizando semántica de pila; esto garantiza que el recuento de referencias se reduzca a cero cuando finalice la función. En este ejemplo se muestra una clase ref básica `Uri`y una función que la utiliza con semántica de pila:

[!code-cpp[cx_classes#06](../cppcx/codesnippet/CPP/classesstructs/class1.cpp#06)]

## <a name="memory-management"></a>Administración de la memoria

Puedes asignar una clase ref en memoria dinámica mediante la palabra clave `ref new` .

[!code-cpp[cx_classes#01](../cppcx/codesnippet/CPP/classesstructs/class1.h#01)]

El operador de tipo "identificador a objeto" ^ se conoce como “sombrero” y es fundamentalmente un puntero inteligente de C++. La memoria a la que apunta se destruye automáticamente cuando el último "hat" sale del ámbito o se establece explícitamente en `nullptr`.

Por definición, una clase ref tiene semántica de referencia. Al asignar una variable de clase ref, se copia el identificador y no el propio objeto. En el ejemplo siguiente, después de la asignación, tanto `myClass` como `myClass2` apuntan a la misma ubicación de memoria.

[!code-cpp[cx_classes#02](../cppcx/codesnippet/CPP/classesstructs/class1.h#02)]

Cuando se crea una instancia de una clase ref de C++/CX , su memoria se inicializa a cero antes de que se llame a su constructor; por tanto, no es necesario inicializar a cero miembros individuales, incluidas las propiedades. Si la clase de C++/CX deriva de una clase de Biblioteca C++ de Windows en tiempo de ejecución (WRL), solo se inicializa a cero la parte de la clase derivada de C++/CX.

### <a name="members"></a>Miembros

Una clase ref puede contener miembros de función `public`, `protected`y `private` ; solo los miembros `public` y `protected` se emiten en metadatos. Las clases anidadas y las clases ref se permiten pero no pueden ser `public`. Los campos públicos no se permiten; los miembros de datos públicos deben declararse como propiedades. Los miembros de datos internos privados o protegidos pueden ser campos. De forma predeterminada, en una clase ref la accesibilidad de todos los miembros es `private`.

Un struct ref es lo mismo que una clase ref, salvo que, de forma predeterminada, sus miembros tienen accesibilidad `public` .

Una `public` clase Ref o un struct Ref se emiten en metadatos, pero para que se puedan usar desde otras aplicaciones plataforma universal de Windows y Windows Runtime componentes, debe tener al menos un constructor público o protegido. Una clase ref pública que tenga un constructor público también se debe declarar como `sealed` para evitar la derivación adicional mediante la interfaz binaria de aplicación (ABI).

Los miembros públicos no pueden declararse como const porque el sistema de tipos Windows Runtime no es compatible con const. Puedes utilizar una propiedad estática para declarar un miembro de datos público con un valor constante.

Cuando defines una clase ref pública o un struct ref público, el compilador aplica los atributos necesarios a la clase y almacena la información en el archivo .winmd de la aplicación. Sin embargo, al definir una clase Ref pública no sellada, aplique manualmente el `Windows::Foundation::Metadata::WebHostHidden` atributo para asegurarse de que la clase no sea visible para plataforma universal de Windows aplicaciones escritas en JavaScript.

Una clase ref puede tener tipos de C++ estándar, incluidos los tipos `const` , en cualquier miembro `private`, `internal`o `protected private` .

Las clases ref públicas que tienen parámetros de tipo no se permiten. No se permiten clases ref genéricas definidas por el usuario. Una clase ref privada, interna o privada protegida puede ser una plantilla.

## <a name="destructors"></a>Destructores

En C++/CX, llamar `delete` a en un destructor público invoca el destructor independientemente del recuento de referencias del objeto. Este comportamiento permite definir un destructor que realiza la limpieza personalizada de recursos no RAII de una manera determinista. Sin embargo, incluso en este caso, el propio objeto no se elimina de la memoria. La memoria del objeto solo se libera cuando el recuento de referencias llega a cero.

Si el destructor de una clase no es público, solo se invoca cuando el recuento de referencias llega a cero. Si se llama `delete` a en un objeto que tiene un destructor privado, el compilador genera la advertencia C4493, que indica que "la expresión de eliminación \<no tiene ningún efecto porque el destructor del nombre de tipo > no tiene accesibilidad" pública "".

Los destructores de clase ref solo pueden declararse del siguiente modo:

- público y virtual (se permite en tipos sellados o no sellados)

- privado protegido y no virtual (solo se permite en tipos no sellados)

- privado y no virtual (solo se permite en tipos sellados)

No se permite ninguna otra combinación de accesibilidad, virtualidad y capacidad de sellado.  Si no declaras explícitamente un destructor, el compilador genera un destructor virtual público si la clase base o cualquier miembro del tipo tienen un destructor público. De lo contrario, el compilador genera un destructor no virtual privado protegido para los tipos no sellados o un destructor no virtual privado para los tipos sellados.

El comportamiento no está definido (undefined) si intentas tener acceso a los miembros de una clase en que ya se haya ejecutado su destructor; lo más probable es que el programa se bloquee. La llamada a `delete t` en un tipo que no tenga un destructor público no tiene ningún efecto. La llamada a `delete this` en un tipo o una clase base que tenga un destructor `private` o `protected private` conocido desde su jerarquía de tipos tampoco tiene ningún efecto.

Al declarar un destructor público, el compilador genera el código para que la clase ref implemente `Platform::IDisposable` y el destructor implemente el método `Dispose` . `Platform::IDisposable`es la C++proyección de/CX `Windows::Foundation::IClosable`de. Nunca debes implementar explícitamente estas interfaces.

## <a name="inheritance"></a>Herencia

Platform::Object es la clase base universal para todas las clases ref. Todas las clases ref se pueden convertir implícitamente en Platform::Object y pueden invalidar [Object::ToString](../cppcx/platform-object-class.md#tostring). Sin embargo, el modelo de herencia de Windows Runtime no se ha diseñado como modelo de herencia general; en C++/CX esto significa que una clase Ref pública definida por el usuario no puede actuar como clase base.

Si vas a crear un control de usuario de XAML y el objeto participa en el sistema de propiedades de dependencia, puedes usar `Windows::UI::Xaml::DependencyObject` como clase base.

Después de que hayas definido una clase no sellada `MyBase` que herede de `DependencyObject`, otras clases ref públicas o privadas de tu componente o aplicación pueden heredar de `MyBase`. La herencia de clases ref públicas solo debe realizarse para admitir reemplazos de métodos virtuales, identidad polimórfica y encapsulación.

No es necesario que una clase ref base privada derive de una clase no sellada existente. Si necesitas una jerarquía de objetos para modelar tu propia estructura de programa o para habilitar la reutilización de código, utiliza clases ref privadas o internas, o todavía mejor, clases de C++ estándar. Puedes exponer la funcionalidad de la jerarquía de objetos privados a través de un contenedor de clases ref públicas o privadas.

Una clase Ref que tenga un constructor público o protegido en C++/CX debe declararse como Sealed. Esta restricción significa que no hay ninguna manera de que las clases escritas en otros lenguajes C# como o Visual Basic hereden de los tipos que se declaran en un componente de C++Windows Runtime escrito en/CX.

Estas son las reglas básicas para la herencia C++en/CX:

- Las clases ref pueden heredar directamente de a lo sumo una clase ref base, pero pueden implementar cualquier número de interfaces.

- Si una clase tiene un constructor público, se debe declarar como sellada para evitar la derivación adicional.

- Puedes crear clases base no selladas públicas que tengan constructores privados protegidos o internos, siempre que la clase base derive directa o indirectamente de una clase base no sellada existente como `Windows::UI::Xaml::DependencyObject`. La herencia de las clases ref definidas por el usuario a través de archivos .winmd no se admite; sin embargo, una clase ref puede heredar de una interfaz que esté definida en otro archivo .winmd. Puede crear clases derivadas a partir de una clase Ref base definida por el usuario solo dentro del mismo Windows Runtime componente o Plataforma universal de Windows aplicación.

- Para las clases ref solo se admite la herencia pública.

   [!code-cpp[cx_classes#08](../cppcx/codesnippet/CPP/classesstructs/class1.h#08)]

En el ejemplo siguiente se muestra cómo exponer una clase ref pública que derive de otras clases ref en una jerarquía de herencia.

[!code-cpp[cx_classes#09](../cppcx/codesnippet/CPP/classesstructs/class1.h#09)]

## <a name="see-also"></a>Vea también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Clases y structs de valor](../cppcx/value-classes-and-structs-c-cx.md)<br/>
[Referencia del lenguaje C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
