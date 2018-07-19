---
title: Propiedades (C++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6393b5e5849ab2198fa8d084c2c1d15838c69bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089564"
---
# <a name="properties-ccx"></a>Propiedades (C++/CX)
Tipos de Windows Runtime exponen los datos públicos como propiedades. El código de cliente tiene acceso a la propiedad como un objeto datamember público. Internamente, la propiedad se implementa como un bloque que contiene un método de descriptor de acceso get, un método de descriptor de acceso set o ambos. Mediante los métodos de descriptor de acceso, puedes realizar acciones adicionales antes o después de recuperar el valor; por ejemplo, puedes desencadenar un evento o realizar comprobaciones de validación.  
  
### <a name="remarks"></a>Comentarios  
 El valor de una propiedad se incluye en una variable privada (conocida como *memoria auxiliar*) que es del mismo tipo que la propiedad. Una propiedad puede contener un descriptor de acceso set, que asigna un valor a la memoria auxiliar, y un descriptor de acceso get, que recupera el valor de la memoria auxiliar. La propiedad es de solo lectura si proporciona solo un descriptor de acceso get, de solo escritura si proporciona solo un descriptor de acceso set, y de lectura y escritura (modificable) si proporciona ambos descriptores de acceso.  
  
 Una propiedad *trivial* es una propiedad de lectura y escritura para la que el compilador implementa automáticamente los descriptores de acceso y la memoria auxiliar. No tienes acceso a la implementación del compilador. Sin embargo, puedes declarar una propiedad personalizada y declarar explícitamente sus descriptores de acceso y su memoria auxiliar. Dentro de un descriptor de acceso, puedes realizar cualquier lógica que se necesite, como la validación de la entrada al descriptor de acceso set, el cálculo de un valor a partir del valor de propiedad, el acceso a una base de datos o el desencadenamiento de un evento cuando la propiedad cambia.  
  
 Cuando se crea una instancia de una clase ref de C++/CX, su memoria se inicializa a cero antes de llamar a su constructor; por tanto, se asigna un valor predeterminado de cero o nullptr a todas las propiedades en el punto de declaración.  
  
### <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo de código se muestra cómo declarar y tener acceso a una propiedad. La primera propiedad, `Name`, se conoce como propiedad *trivial* porque el compilador genera automáticamente un descriptor de acceso `set` , un descriptor de acceso `get` y una memoria auxiliar.  
  
 La segunda propiedad, `Doctor`, es una propiedad de solo lectura porque especifica un *bloque de propiedad* que declara explícitamente solo un descriptor de acceso `get` . Dado que se declara el bloque de la propiedad, debes declarar explícitamente una memoria auxiliar, es decir, la variable String^ privada, `doctor_`. Normalmente, una propiedad de solo lectura simplemente devuelve el valor de la memoria auxiliar. Solo la propia clase puede establecer el valor de la memoria auxiliar, normalmente en el constructor.  
  
 La tercera propiedad, `Quantity`, es una propiedad de lectura y escritura porque declara un bloque de propiedad que declara tanto un descriptor de acceso `set` como un descriptor de acceso `get` .  
  
 El descriptor de acceso `set` realiza una prueba de validez definida por el usuario en el valor asignado. A diferencia de C#, aquí el nombre *value* es simplemente el identificador del parámetro en el descriptor de acceso `set` ; no es una palabra clave. Si *value* no es mayor que cero, se produce una excepción Platform::InvalidArgumentException. De lo contrario, la memoria auxiliar, `quantity_`, se actualiza con el valor asignado.  
  
 Ten en cuenta que no se puede inicializar una propiedad en una lista de miembros. Por supuesto, puedes inicializar variables de memoria auxiliar en una lista de miembros.  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)