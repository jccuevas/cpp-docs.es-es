---
title: Uso de la pila | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6e3aa8d01dcc85b6c37684ccccaf82c84d8dfb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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