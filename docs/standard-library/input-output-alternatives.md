---
title: Alternativas de entrada/salida | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], alternatives
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4999aa9e7e1c5a2578f09bcaebb5e4a7fa934155
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="inputoutput-alternatives"></a>Alternativas de entrada/salida
Visual C++ proporciona varias alternativas para la programación de E/S:  
  
-   E/S directa y no almacenada en búfer de la biblioteca en tiempo de ejecución de C.  
  
-   E/S de secuencia de la biblioteca en tiempo de ejecución de ANSI C.  
  
-   E/S directa de consola y puerto.  
  
-   Biblioteca MFC (Microsoft Foundation Class).  
  
-   Biblioteca estándar de Microsoft C++.  
  
 Las clases iostream son útiles para la E/S de texto con formato almacenada en búfer. También son útiles para la E/S binaria o no almacenada en búfer si necesita una interfaz de programación en C++ y decide no usar la biblioteca MFC (Microsoft Foundation Class). Las clases iostream son una alternativa de E/S orientada a objetos que se puede usar en lugar de las funciones en tiempo de ejecución de C.  
  
 Puede usar las clases iostream con el sistema operativo Microsoft Windows. Los flujos de cadenas y archivos funcionan sin restricciones, pero los objetos de flujo de modo de carácter `cin`, `cout`, `cerr` y `clog` no son coherentes con la interfaz gráfica de usuario de Windows. También puede derivar clases de flujo personalizadas que interactúan directamente con el entorno de Windows.  
  
## <a name="see-also"></a>Vea también  
 [¿Qué es un flujo?](../standard-library/what-a-stream-is.md)

