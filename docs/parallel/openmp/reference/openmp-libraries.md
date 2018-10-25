---
title: Bibliotecas de OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 7620b0ea710a5474fbbbf614691ceeb1e5cc945e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062007"
---
# <a name="openmp-libraries"></a>Bibliotecas de OpenMP

Describe los archivos .lib que componen las bibliotecas en tiempo de ejecución OpenMP en Visual C++.

Las bibliotecas siguientes contienen las funciones de biblioteca en tiempo de ejecución de Visual C++ de OpenMP.

|Biblioteca de tiempo de ejecución de OpenMP|Características|
|------------------------------|---------------------|
|VCOMP. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMP. LIB).|
|VCOMPD. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMPD. TAPA) (depurar)|

Si está definido _DEBUG en una compilación y si `#include omp.h` está en el código fuente, VCOMPD. LIB será lib de forma predeterminada. En caso contrario, VCOMP. Se usará LIB.

Puede usar [/NODEFAULTLIB (Omitir bibliotecas)](../../../build/reference/nodefaultlib-ignore-libraries.md) quitar lib predeterminado y un vínculo explícito con lib de su elección.

Los archivos DLL de OpenMP se encuentran en el directorio del paquete redistribuible de Visual C++ y deba distribuirse con aplicaciones que usan OpenMP.

## <a name="see-also"></a>Vea también

[Referencia de la biblioteca](openmp-library-reference.md)
