---
title: Ventajas e inconvenientes del método utilizado para el vínculo a la biblioteca CRT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2835e88da11b8d8332226080eb860afd41c0702
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Ventajas e inconvenientes del método utilizado para el vínculo a la biblioteca CRT
Puede vincular el proyecto con la biblioteca CRT dinámica o estáticamente. En la tabla siguiente se describe las ventajas y los inconvenientes de elegir qué método utilizar.  
  
|Método|Prestación|Contrapartida|  
|------------|-------------|--------------|  
|Vincular estáticamente a CRT<br /><br /> (**Biblioteca en tiempo de ejecución** establecido en **uniproceso**)|El archivo DLL de CRT no es necesario en el sistema donde se ejecutará la imagen.|Unos 25 KB de código de inicio se agrega a la imagen, aumentar sustancialmente su tamaño.|  
|Vinculación dinámica a la biblioteca CRT<br /><br /> (**Biblioteca en tiempo de ejecución** establecido en **multiproceso**)|La imagen no requiere código de inicio de CRT, por lo que es mucho más pequeño.|El archivo DLL de CRT deben estar en el sistema que ejecuta la imagen.|  
  
 El tema [vinculación a CRT en un proyecto ATL](../atl/linking-to-the-crt-in-your-atl-project.md) se describe cómo seleccionar el modo en que se va a vincular a CRT.  
  
## <a name="see-also"></a>Vea también  
 [Programar con ATL y el código de tiempo de ejecución de C](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Archivos DLL y el comportamiento de la biblioteca de tiempo de ejecución de Visual C++](../build/run-time-library-behavior.md)   
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)

