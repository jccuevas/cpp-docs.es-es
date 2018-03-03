---
title: "Cómo: crear y utilizar instancias de weak_ptr | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e51e523540e14905bef17edd52205c4d2102afa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Cómo: Crear y usar instancias de weak_ptr
A veces, un objeto debe almacenar una manera de tener acceso al objeto subyacente de un `shared_ptr` sin causar que el recuento de referencias va a incrementar. Normalmente, esta situación se produce cuando tienen referencias cíclicas entre `shared_ptr` instancias.  
  
 Es el mejor diseño evitar la propiedad compartida de punteros siempre que pueda. Sin embargo, si se debe compartir la propiedad de `shared_ptr` instancias, evite las referencias cíclicas entre ellos. Una vez referencias cíclicas inevitable o incluso preferible por algún motivo, usar `weak_ptr` para conceder a uno o varios de los propietarios de una referencia débil a otro `shared_ptr`. Mediante el uso de un `weak_ptr`, puede crear un `shared_ptr` que se une a un conjunto existente de instancias relacionadas, pero solo si el recurso de memoria subyacente sigue siendo válido. Un `weak_ptr` propio no participar en el recuento de referencias y, por lo tanto, no puede impedir que el recuento de referencias va a cero. Sin embargo, puede usar un `weak_ptr` para intentar obtener una nueva copia de la `shared_ptr` con que se inicializó. Si ya se ha eliminado la memoria, un **bad_weak_ptr** se produce la excepción. Si la memoria todavía es válida, el nuevo puntero compartido incrementa el recuento de referencias y garantiza que la memoria sea válida tanto en cuanto la `shared_ptr` variable permanece en el ámbito.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra un caso donde `weak_ptr` se utiliza para garantizar la correcta eliminación de objetos que tienen dependencias circulares. Examinar el ejemplo, suponga que se ha creado solo después de que se tuvieron en cuenta soluciones alternativas. El `Controller` objetos representan algunos aspectos de un proceso de máquina y funcionan de forma independiente. Cada controlador debe ser capaz de consultar el estado de los demás controladores en cualquier momento, y cada uno de ellos contiene una privada `vector<weak_ptr<Controller>>` para este propósito. Cada vector contiene una referencia circular y por lo tanto, `weak_ptr` las instancias se utilizan en lugar de `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
```Output  
Creating Controller0Creating Controller1Creating Controller2Creating Controller3Creating Controller4push_back to v[0]: 1push_back to v[0]: 2push_back to v[0]: 3push_back to v[0]: 4push_back to v[1]: 0push_back to v[1]: 2push_back to v[1]: 3push_back to v[1]: 4push_back to v[2]: 0push_back to v[2]: 1push_back to v[2]: 3push_back to v[2]: 4push_back to v[3]: 0push_back to v[3]: 1push_back to v[3]: 2push_back to v[3]: 4push_back to v[4]: 0push_back to v[4]: 1push_back to v[4]: 2push_back to v[4]: 3use_count = 1Status of 1 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 3 = OnDestroying Controller0Destroying Controller1Destroying Controller2Destroying Controller3Destroying Controller4Press any key  
```  
  
 Como experimento, modifique el vector `others` sea un `vector<shared_ptr<Controller>>`y, a continuación, en la salida, tenga en cuenta que ninguna destructores se invocan cuando `TestRun` devuelve.  
  
## <a name="see-also"></a>Vea también  
 [Punteros inteligentes](../cpp/smart-pointers-modern-cpp.md)