---
title: Procedimiento Crear y usar instancias de weak_ptr
ms.custom: how-to
ms.date: 09/18/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: e5d1b13d894a617ca514e26f14fde3f514540d34
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127174"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Procedimiento Crear y usar instancias de weak_ptr

A veces, un objeto debe almacenar una manera de tener acceso al objeto `shared_ptr` subyacente de un sin provocar que se incremente el recuento de referencias. Normalmente, esta situación se produce cuando hay referencias cíclicas `shared_ptr` entre instancias.

El mejor diseño es evitar la propiedad compartida de los punteros siempre que sea posible. Sin embargo, si debe tener la propiedad compartida `shared_ptr` de las instancias, evite las referencias cíclicas entre ellas. Cuando las referencias cíclicas son inevitables, o incluso preferibles por alguna razón `weak_ptr` , use para dar a uno o varios propietarios una referencia débil a `shared_ptr`otro. Mediante el uso `weak_ptr`de, puede crear un `shared_ptr` que se una a un conjunto existente de instancias relacionadas, pero solo si el recurso de memoria subyacente todavía es válido. Una `weak_ptr` propiamente dicha no participa en el recuento de referencias y, por lo tanto, no puede impedir que el recuento de referencias pase a cero. Sin embargo, puede utilizar un `weak_ptr` para intentar obtener una nueva copia de con la `shared_ptr` que se inicializó. Si ya se ha eliminado la memoria, el `weak_ptr`operador bool de devuelve `false`. Si la memoria sigue siendo válida, el nuevo puntero compartido incrementa el recuento de referencias y garantiza que la memoria será válida siempre y cuando la `shared_ptr` variable permanezca en el ámbito.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra `weak_ptr` un caso en el que se usa para garantizar la eliminación correcta de los objetos que tienen dependencias circulares. Cuando examine el ejemplo, supongamos que se creó solo después de que se tuvieran en cuenta soluciones alternativas. Los `Controller` objetos representan algún aspecto de un proceso de equipo y funcionan de manera independiente. Cada controlador debe ser capaz de consultar el estado de los demás controladores en cualquier momento, y cada uno de ellos contiene `vector<weak_ptr<Controller>>` un privado para este fin. Cada vector contiene una referencia circular y, por lo `weak_ptr` tanto, se usan instancias en `shared_ptr`lugar de.

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

Como experimento, modifique el vector `others` para que sea un `vector<shared_ptr<Controller>>`y, a continuación, en la salida, observe que no se invoca ningún destructor cuando `TestRun` devuelve.

## <a name="see-also"></a>Vea también

[Punteros inteligentes (C++ moderno)](../cpp/smart-pointers-modern-cpp.md)
