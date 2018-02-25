---
title: Bibliotecas de OpenMP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 760e7d138ab71244419ff71960948d4d10f125eb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="openmp-libraries"></a>Bibliotecas de OpenMP
Describe los archivos .lib que componen las bibliotecas en tiempo de ejecución OpenMP en Visual C++.  
  
 Las bibliotecas siguientes contienen las funciones de biblioteca en tiempo de ejecución de OpenMP de Visual C++.  
  
|Biblioteca de tiempo de ejecución de OpenMP|Características|  
|------------------------------|---------------------|  
|VCOMP.LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMP. LIB).|  
|VCOMPD.LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMPD. TAPA) (depurar)|  
  
 Si se define _DEBUG en una compilación y `#include omp.h` se encuentra en el código fuente, VCOMPD. LIB será la biblioteca predeterminada. En caso contrario, VCOMP. Se usará LIB.  
  
 Puede usar [/NODEFAULTLIB (Omitir bibliotecas)](../../../build/reference/nodefaultlib-ignore-libraries.md) para quitar la biblioteca predeterminada y se vincula explícitamente con la herramienta lib de su elección.  
  
 Los archivos DLL de OpenMP están en el directorio del paquete redistribuible de Visual C++ y se deben distribuir con las aplicaciones que usan OpenMP.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca](../../../parallel/openmp/reference/openmp-library-reference.md)