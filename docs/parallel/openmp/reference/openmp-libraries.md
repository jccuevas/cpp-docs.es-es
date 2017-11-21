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
ms.openlocfilehash: faac1a2a081a2ce0b02f2008bf3766537557df28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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