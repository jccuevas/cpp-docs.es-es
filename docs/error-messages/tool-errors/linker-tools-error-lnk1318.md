---
title: Error de las herramientas del vinculador LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: a61c11a9cbb25fea6fddc0bf1c5c4c2a7af1cf4f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183584"
---
# <a name="linker-tools-error-lnk1318"></a>Error de las herramientas del vinculador LNK1318

> Error de PDB inesperado. *causa* '*detalles*'

El enlazador ha encontrado un error inesperado al abrir, leer o escribir en un archivo PDB.

Este mensaje de error se genera para problemas poco comunes en los archivos PDB. La *causa* y los *detalles* representan la información disponible para el vinculador cuando se produjo el error. Esto puede no ser muy útil, ya que los errores comunes al trabajar con archivos PDB tienen mensajes de error independientes y más informativos.

Dado que el origen del error no es habitual, solo hay consejos genéricos disponibles para resolver este problema:

- Realice una operación de limpieza en los directorios de compilación y, a continuación, realice una compilación completa de la solución.

- Reinicie el equipo, o Compruebe si hay procesos de mspdbsrv. exe aislados o bloqueados y elimínelos en TaskManager.

- Desactive las comprobaciones del antivirus en los directorios del proyecto.

- Use la opción del compilador [/ZF](../../build/reference/zf.md) si usa [/MP](../../build/reference/mp-build-with-multiple-processes.md) con MSBuild u otro proceso de compilación en paralelo.

- Intente compilar con el conjunto de herramientas hospedado de 64 bits.

- Serializar la vinculación para mitigar los problemas de vínculos paralelos si es necesario. Este error puede producirse si se inicia mspdbsrv. exe en una instancia de Link y se cierra antes de que otra instancia de Link se realice usando. El inconveniente de esta corrección es que las compilaciones del proyecto pueden tardar mucho más tiempo en completarse.
