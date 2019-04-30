---
title: Referencia de la biblioteca de OpenMP
ms.date: 03/20/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: 6f4bbeca54bff1fc44a3576362edca9c30926d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362522"
---
# <a name="openmp-library-reference"></a>Referencia de la biblioteca de OpenMP

Proporciona vínculos a las construcciones que se usan en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye las siguientes construcciones.

|Construcción|Descripción|
|---------------|-----------------|
|[Directivas](openmp-directives.md)|Proporciona vínculos a las directivas que se utilizan en la API de OpenMP.|
|[Cláusulas](openmp-directives.md)|Proporciona vínculos a las cláusulas que se utilizan en la API de OpenMP.|
|[Funciones](openmp-functions.md)|Proporciona vínculos a las funciones utilizadas en la API de OpenMP.|
|[Variables de entorno](openmp-environment-variables.md)|Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.|

El objeto Visual C++ funciones de biblioteca en tiempo de ejecución de OpenMP se encuentran en las siguientes bibliotecas.

|Biblioteca de tiempo de ejecución de OpenMP|Características|
|------------------------------|---------------------|
|VCOMP. LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMP. LIB).|
|VCOMPD.LIB|Vínculo multiproceso, dinámico (biblioteca de importación para VCOMPD. TAPA) (depurar)|

Si está definido _DEBUG en una compilación y si `#include omp.h` está en el código fuente, VCOMPD. LIB será lib de forma predeterminada, en caso contrario, VCOMP. Se usará LIB.

Puede usar [/NODEFAULTLIB (Omitir bibliotecas)](../../../build/reference/nodefaultlib-ignore-libraries.md) quitar lib predeterminado y un vínculo explícito con lib de su elección.

Los archivos DLL de OpenMP se encuentran en el directorio del paquete redistribuible de Visual C++ y deba distribuirse con aplicaciones que usan OpenMP.

## <a name="see-also"></a>Vea también

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)