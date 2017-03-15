---
title: "¿Qué es un flujo? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 75c23582cbbb42a417a7a5effdb879300c2a7732
ms.lasthandoff: 02/24/2017

---
# <a name="what-a-stream-is"></a>¿Qué es un flujo?
Al igual que C, C++ no tiene capacidad integrada de entrada y salida. Pero todos los compiladores de C++ incluyen un paquete sistemático de E/S orientado a objetos, conocido como las clases iostream. La secuencia es el concepto central de las clases iostream. Puede pensar en un objeto de secuencia como en un archivo inteligente que actúa como origen y destino de bytes. Las características de una secuencia se determinan por su clase y por operadores de inserción y extracción personalizados.  
  
 A través de los controladores de dispositivo, el sistema operativo de disco se ocupa del teclado, la pantalla, la impresora y los puertos de comunicación como archivos extendidos. Las clases iostream interactúan con estos archivos extendidos. Las clases integradas admiten la lectura y escritura en la memoria con una sintaxis idéntica a la de E/S de disco, lo que facilita la derivación de las clases de secuencia.  
  
## <a name="in-this-section"></a>En esta sección  
 [Alternativas de entrada/salida](../standard-library/input-output-alternatives.md)  
  
## <a name="see-also"></a>Vea también  
 [Programación con iostream](../standard-library/iostream-programming.md)


