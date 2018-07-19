---
title: Uso de la pila | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6f711636089a6f2966002002220aac88cebe17a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379863"
---
# <a name="stack-usage"></a>Uso de las pilas
Toda la memoria más allá de la dirección actual de RSP se considera volátil: el sistema operativo o un depurador, puede sobrescribir esta memoria durante una sesión de depuración de usuario o un controlador de interrupción. Por lo tanto, se debe establecer siempre RSP antes de intentar leer o escribir valores en un marco de pila.  
  
 En esta sección se explica la asignación de espacio de pila para las variables locales y la **alloca** intrínseco.  
  
-   [Asignación de espacio de pila](../build/stack-allocation.md)  
  
-   [Construcción del área de pila para el parámetro dinámico](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Tipos de funciones](../build/function-types.md)  
  
-   [Alineación de malloc](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)