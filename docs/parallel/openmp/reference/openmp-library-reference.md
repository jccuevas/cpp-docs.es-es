---
title: Referencia de la biblioteca de OpenMP
ms.date: 07/30/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: c63ae5ba7f04d8ee6bd02418792804373fa71e6b
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72348224"
---
# <a name="openmp-library-reference"></a>Referencia de la biblioteca de OpenMP

Proporciona vínculos a las construcciones usadas en la API de OpenMP.

La implementación C++ visual del estándar de OpenMP incluye las siguientes construcciones.

|Construcción|Descripción|
|---------------|-----------------|
|[Directivas](openmp-directives.md)|Proporciona vínculos a las directivas usadas en la API de OpenMP.|
|[Cláusulas](openmp-clauses.md)|Proporciona vínculos a las cláusulas usadas en la API de OpenMP.|
|[Funciones](openmp-functions.md)|Proporciona vínculos a las funciones que se usan en la API de OpenMP.|
|[Variables de entorno](openmp-environment-variables.md)|Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.|

Las funciones C++ de la biblioteca en tiempo de ejecución de Visual OpenMP están contenidas en las bibliotecas siguientes.

|Biblioteca en tiempo de ejecución de OpenMP|Características|
|------------------------------|---------------------|
|VCOMP. OBJ|Vínculo multiproceso y dinámico (biblioteca de importación para VCOMP. LIB).|
|VCOMPD. OBJ|Vínculo multiproceso y dinámico (biblioteca de importación para VCOMPD. LID) (depurar)|

Si se define _ debug en una compilación y si `#include <omp.h>` está en código fuente, VCOMPD. LIB será la biblioteca predeterminada, de lo contrario, VCOMP. Se usará LIB.

Puede usar [/NODEFAULTLIB (omitir bibliotecas)](../../../build/reference/nodefaultlib-ignore-libraries.md) para quitar el lib predeterminado y vincularlo explícitamente con el lib de su elección.

Los archivos dll de OpenMP se encuentran C++ en el directorio redistribuible visual y deben distribuirse con aplicaciones que usan OpenMP.

## <a name="see-also"></a>Vea también

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
