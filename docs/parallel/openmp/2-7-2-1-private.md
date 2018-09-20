---
title: 2.7.2.1 privada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d06650a784b5b59405f446f4701918393b21fa3b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387242"
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