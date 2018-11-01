---
title: 2.7.2.1 private
ms.date: 11/04/2016
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
ms.openlocfilehash: c1a2560eb80c848605698c435e3a0f0f7e66b75a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536960"
---
# <a name="2721-private"></a>2.7.2.1 private

El `private` cláusula declara las variables en la lista de variables a ser privada para cada subproceso en un equipo. La sintaxis de la `private` cláusula es como sigue:

```
private(variable-list)
```

El comportamiento de una variable especificada en un `private` es la siguiente cláusula. Se asigna un nuevo objeto con una duración de almacenamiento automática para la construcción. El tamaño y la alineación del nuevo objeto se determinan por el tipo de la variable. Esta asignación se produce una vez para cada subproceso en el equipo y se invoca un constructor predeterminado para un objeto de clase si es necesario; en caso contrario, el valor inicial es indeterminado.  El objeto original al que hace referencia la variable tiene un valor indeterminado al entrar en la construcción, no se debe modificar dentro de la extensión de la construcción dinámica y tiene un valor indeterminado al salir de la construcción.

En la medida léxica de la construcción de la directiva, el nuevo objeto privado asignado por el subproceso hace referencia a la variable.

Las restricciones para el `private` cláusula son los siguientes:

- Una variable con un tipo de clase que se especifica en un `private` cláusula debe tener un constructor predeterminado accesible y no ambigua.

- Una variable especificada en un `private` cláusula no debe tener un **const**-calificado tipo a menos que tenga una clase de tipo con un `mutable` miembro.

- Una variable especificada en un `private` cláusula no debe tener un tipo incompleto ni un tipo de referencia.

- Las variables que aparecen en la `reduction` cláusula de una **paralelo** directiva no se puede especificar en un `private` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.