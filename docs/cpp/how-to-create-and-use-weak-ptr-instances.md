---
title: 'Cómo: Crear y usar instancias de weak_ptr'
ms.custom: how-to
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: c3f788a23acf30fac84757f8cd4430f128df67af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478200"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Cómo: Crear y usar instancias de weak_ptr

A veces, un objeto debe almacenar una manera de obtener acceso al objeto subyacente de un `shared_ptr` sin provocar el recuento de referencias se incremente. Normalmente, esta situación se produce cuando hay referencias cíclicas entre `shared_ptr` instancias.

Es el mejor diseño evitar la propiedad compartida de punteros siempre que pueda. Sin embargo, si debe haber compartido la propiedad de `shared_ptr` instancias, evite las referencias cíclicas entre ellas. Cuando las referencias cíclicas son inevitables, o incluso preferibles por alguna razón, utilice `weak_ptr` para dar a uno o varios de los propietarios una referencia débil a otro `shared_ptr`. Mediante el uso de un `weak_ptr`, puede crear un `shared_ptr` que une a un conjunto existente de instancias relacionadas, pero solo si el recurso de memoria subyacente sigue siendo válido. Un `weak_ptr` no participar en el recuento de referencias y, por lo tanto, que no impide que el recuento de referencias vaya hacia cero. Sin embargo, puede usar un `weak_ptr` para intentar obtener una copia nueva de la `shared_ptr` con que se ha inicializado. Si ya se ha eliminado la memoria, un `bad_weak_ptr` es una excepción. Si la memoria es aún válida, el nuevo puntero compartido incrementa el recuento de referencias y garantiza que la memoria será válida siempre y cuando el `shared_ptr` variable permanezca dentro del ámbito.

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente muestra un caso donde `weak_ptr` sirve para garantizar la eliminación correcta de los objetos que tienen dependencias circulares. Al examinar el ejemplo, suponga que se creó después de considerar las soluciones alternativas. El `Controller` objetos representan algún aspecto de un proceso de máquina y funcionan independientemente. Cada controlador debe ser capaz de consultar el estado de los demás controladores en cualquier momento, y cada uno de ellos contiene una privada `vector<weak_ptr<Controller>>` para este propósito. Cada vector contiene una referencia circular y por lo tanto, `weak_ptr` las instancias se utilizan en lugar de `shared_ptr`.

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
Status of 0 = O
nStatus of 1 = On
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

Como experimento, modifique el vector `others` sea un `vector<shared_ptr<Controller>>`y, a continuación, en la salida, observe que no se invoca ningún destructor cuando `TestRun` devuelve.

## <a name="see-also"></a>Vea también

[Punteros inteligentes](../cpp/smart-pointers-modern-cpp.md)