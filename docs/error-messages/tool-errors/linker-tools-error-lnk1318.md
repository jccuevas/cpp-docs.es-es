---
title: LNK1318 de Error de las herramientas del vinculador
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648739"
---
# <a name="linker-tools-error-lnk1318"></a>LNK1318 de Error de las herramientas del vinculador

> Error inesperado de PDB; *provocar* '*detalles*'

El vinculador encontró un error inesperado al abrir, leer o escribir en un archivo PDB.

Este mensaje de error se produce para problemas poco habituales en archivos PDB. El *provocar* y *detalles* representan la información disponible al vinculador cuando se produjo el error. Esto puede no ser muy útil, como errores comunes al trabajar con archivos PDB tiene mensajes de error más informativo independiente.

Dado que el origen del error es poco habitual, hay sólo genérico consejos disponibles para resolver este problema:

- Realizar una operación de limpieza en los directorios de compilación y, a continuación, realice una compilación completa de la solución.

- Reinicie el equipo, o busque los procesos bloqueados o extraviados mspdbsrv.exe y eliminarlos en TaskManager.

- Desactivar las comprobaciones de antivirus en los directorios de proyecto.

- Use la [/Zf](../../build/reference/zf.md) opción del compilador si usa [/MP](../../build/reference/mp-build-with-multiple-processes.md) con MSBuild u otro paralelas de proceso de compilación.

- Intente compilar con el conjunto de herramientas hospedado de 64 bits.

- Serializar vinculación para mitigar los problemas de vínculo paralelo si es necesario. Este error puede producirse si se inicia una instancia de vínculo mspdbsrv.exe y se apaga antes de realiza otra instancia de vínculo con él. La desventaja de esta corrección es que las compilaciones de proyecto pueden tardar mucho tiempo en completarse.