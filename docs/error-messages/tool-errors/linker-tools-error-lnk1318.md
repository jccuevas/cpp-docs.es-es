---
title: Error LNK1318 las herramientas del vinculador | Documentos de Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1318
dev_langs:
- C++
helpviewer_keywords:
- LNK1318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364c819c6ec2bf6e1195011eced6e6ad1699877b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570710"
---
# <a name="linker-tools-error-lnk1318"></a>LNK1318 de Error de herramientas del vinculador

> Error inesperado de PDB; *provocar* '*detalles*'

El vinculador encontró un error inesperado al abrir, leer o escribir en un archivo PDB.

Este mensaje de error se genera para problemas poco habituales en archivos PDB. El *provocar* y *detalles* representan la información disponible al vinculador cuando se produjo el error. Esto puede no ser muy útil, como los errores comunes al trabajar con archivos PDB tiene mensajes de error más informativo, independiente.

Dado que el origen del error es poco habitual, hay únicamente asesoramiento en materia genérico disponible para resolver este problema:

- Realizar una operación de limpieza en los directorios de compilación y, a continuación, realice una compilación completa de la solución.

- Reinicie el equipo, o compruebe si hay procesos de mspdbsrv.exe extraviados o se ha bloqueado y eliminarlos en TaskManager.

- Desactivar las comprobaciones antivirus en los directorios del proyecto.

- Use la [/Zf](../../build/reference/zf.md) opción del compilador si usa [/MP](../../build/reference/mp-build-with-multiple-processes.md) proceso de compilación con MSBuild u otro paralelo.

- Intente compilar utilizando el conjunto de herramientas hospedado de 64 bits.

- La serialización de vinculación para mitigar los problemas de vínculo paralelo si es necesario. Este error puede generarse si mspdbsrv.exe se inicia una instancia de vínculo y se apaga antes de que otra instancia de vínculo se lleva a cabo con él. La desventaja de esta revisión es que las compilaciones de proyecto pueden tardar mucho tiempo en completarse.