---
title: Bibliotecas de OpenMP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46bd287ff8a020a4d5d7775afdb12f5571d43294
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694776"
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