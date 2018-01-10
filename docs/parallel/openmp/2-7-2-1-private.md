---
title: 2.7.2.1 privada | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a08faf39ab2f82d76a936c216ba6707bee5c240
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="2721-private"></a>2.7.2.1 private
El `private` cláusula declara las variables de la lista de variables a ser privada para cada subproceso de un equipo. La sintaxis de la `private` cláusula es como sigue:  
  
```  
private(variable-list)  
```  
  
 El comportamiento de una variable especificada en un `private` cláusula es como sigue. Se asigna un nuevo objeto con una duración de almacenamiento automática para la construcción. El tamaño y la alineación del nuevo objeto se determinan por el tipo de la variable. Esta asignación se produce una vez para cada subproceso en el equipo y se invoca un constructor predeterminado para un objeto de clase, si es necesario; en caso contrario, el valor inicial es indeterminado.  El objeto original al que hace referencia la variable tiene un valor indeterminado sobre las entradas a la construcción, no debe modificarse en la extensión dinámica de la construcción y tiene un valor indeterminado al salir de la construcción.  
  
 En la extensión léxica de la construcción de la directiva, el nuevo objeto privado asignado por el subproceso hace referencia a la variable.  
  
 Las restricciones a la `private` cláusula son los siguientes:  
  
-   Una variable con un tipo de clase que se especifica en un `private` cláusula debe tener un constructor predeterminado accesible y no ambigua.  
  
-   Una variable especificada en un `private` cláusula no debe tener un **const**-calificado tipo a menos que tenga una clase de tipo con un `mutable` miembro.  
  
-   Una variable especificada en un `private` cláusula no debe tener un tipo incompleto ni un tipo de referencia.  
  
-   Las variables que aparecen en la `reduction` cláusula de una **paralelo** directiva no se puede especificar en un `private` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.