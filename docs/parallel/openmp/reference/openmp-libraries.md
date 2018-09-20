---
title: Bibliotecas de OpenMP | Microsoft Docs
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
ms.openlocfilehash: c9a4ccfefeaeb9446731027db44b849233bfefd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391220"
---
# <a name="openmp-libraries"></a>Bibliotecas de OpenMP

Describe los archivos .lib que componen las bibliotecas en tiempo de ejecución OpenMP en Visual C++.

Las bibliotecas siguientes contienen las funciones de biblioteca en tiempo de ejecución de Visual C++ de OpenMP.

|Biblioteca de tiempo de ejecución de OpenMP|Características|
|------------------------------|---------------------|
|VCOMP. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMP. LIB).|
|VCOMPD. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMPD. TAPA) (depurar)|

Si está definido _DEBUG en una compilación y si `#include omp.h` está en el código fuente, VCOMPD. LIB será lib de forma predeterminada. En caso contrario, VCOMP. Se usará LIB.

Puede usar [/NODEFAULTLIB (Ignore Libraries)](../../../build/reference/nodefaultlib-ignore-libraries.md) quitar lib predeterminado y un vínculo explícito con lib de su elección.

Los archivos DLL de OpenMP se encuentran en el directorio del paquete redistribuible de Visual C++ y deba distribuirse con aplicaciones que usan OpenMP.

## <a name="see-also"></a>Vea también

[Referencia de la biblioteca](../../../parallel/openmp/reference/openmp-library-reference.md)