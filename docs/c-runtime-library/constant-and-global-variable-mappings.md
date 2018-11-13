---
title: Asignaciones de constantes y de variables globales
ms.date: 11/04/2016
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
ms.openlocfilehash: 0f4e41e652cc1154b3bbc1ae3ca20c143e2745ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646191"
---
# <a name="constant-and-global-variable-mappings"></a>Asignaciones de constantes y de variables globales

Estas asignaciones de constantes y de variables globales de texto genérico y de tipo estándar se definen en TCHAR.H y dependen de que la constante `_UNICODE` o `_MBCS` se haya definido en el programa.

### <a name="generic-text-constant-and-global-variable-mappings"></a>Asignaciones de constantes y de variables globales de texto genérico

|Texto genérico: nombre de objeto|SBCS (_UNICODE, _MBCS no definidos)|_MBCS definido|_UNICODE definido|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>Vea también

[Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md)<br/>
[Asignaciones de tipos de datos](../c-runtime-library/data-type-mappings.md)<br/>
[Asignaciones de rutinas](../c-runtime-library/routine-mappings.md)<br/>
[Ejemplo de programa de texto genérico](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Usar asignaciones de texto genérico](../c-runtime-library/using-generic-text-mappings.md)