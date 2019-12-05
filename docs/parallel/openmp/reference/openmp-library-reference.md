---
title: Referencia de la biblioteca de OpenMP
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810740"
---
# <a name="openmp-library-reference"></a>Referencia de la biblioteca de OpenMP

Proporciona vínculos a las construcciones usadas en la API de OpenMP.

La implementación C++ visual del estándar de OpenMP incluye las siguientes construcciones.

|Construir|Descripción|
|---------------|-----------------|
|[Directivas](openmp-directives.md)|Proporciona vínculos a las directivas usadas en la API de OpenMP.|
|[Cláusulas](openmp-clauses.md)|Proporciona vínculos a las cláusulas usadas en la API de OpenMP.|
|[Funciones](openmp-functions.md)|Proporciona vínculos a las funciones que se usan en la API de OpenMP.|
|[Variables de entorno](openmp-environment-variables.md)|Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.|

Las funciones C++ de la biblioteca en tiempo de ejecución de Visual OpenMP están contenidas en las bibliotecas siguientes.

|Biblioteca en tiempo de ejecución de OpenMP|Características|
|------------------------------|---------------------|
|VCOMP. OBJ|Vínculo multiproceso y dinámico (biblioteca de importación para VCOMP140. DLL).|
|VCOMPD. OBJ|Vínculo multiproceso y dinámico (biblioteca de importación para VCOMP140D. DLL) (depurar)|

Si _DEBUG se define en una compilación y si `#include <omp.h>` está en código fuente, VCOMPD. LIB será la biblioteca predeterminada, de lo contrario, VCOMP. Se usará LIB.

Puede usar [/NODEFAULTLIB (omitir bibliotecas)](../../../build/reference/nodefaultlib-ignore-libraries.md) para quitar el lib predeterminado y vincularlo explícitamente con el lib de su elección.

Los archivos dll de OpenMP se encuentran C++ en el directorio redistribuible visual y deben distribuirse con aplicaciones que usan OpenMP.

## <a name="see-also"></a>Vea también

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
