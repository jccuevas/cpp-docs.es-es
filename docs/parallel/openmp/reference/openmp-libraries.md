---
title: Bibliotecas de OpenMP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c0f009c26789fd771d55dab5fcfe5f342aa03b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-libraries"></a>Bibliotecas de OpenMP
Describe los archivos .lib que componen las bibliotecas en tiempo de ejecución OpenMP en Visual C++.  
  
 Las bibliotecas siguientes contienen las funciones de biblioteca en tiempo de ejecución de OpenMP de Visual C++.  
  
|Biblioteca de tiempo de ejecución de OpenMP|Características|  
|------------------------------|---------------------|  
|VCOMP. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMP. LIB).|  
|VCOMPD. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMPD. TAPA) (depurar)|  
  
 Si se define _DEBUG en una compilación y `#include omp.h` se encuentra en el código fuente, VCOMPD. LIB será la biblioteca predeterminada. En caso contrario, VCOMP. Se usará LIB.  
  
 Puede usar [/NODEFAULTLIB (Omitir bibliotecas)](../../../build/reference/nodefaultlib-ignore-libraries.md) para quitar la biblioteca predeterminada y se vincula explícitamente con la herramienta lib de su elección.  
  
 Los archivos DLL de OpenMP están en el directorio del paquete redistribuible de Visual C++ y se deben distribuir con las aplicaciones que usan OpenMP.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca](../../../parallel/openmp/reference/openmp-library-reference.md)