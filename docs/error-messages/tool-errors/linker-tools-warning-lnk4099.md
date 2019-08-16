---
title: Advertencia de las herramientas del vinculador LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: dcf4d44c3a0b5b10035af763040c2912afc8c6f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310895"
---
# <a name="linker-tools-warning-lnk4099"></a>Advertencia de las herramientas del vinculador LNK4099

No se encontró PDB 'filename' con 'objeto/library' o 'path'; vinculación de objetos como si no hay información de depuración

El vinculador no pudo encontrar el archivo PDB. Copiar en el directorio que contiene `object/library`.

Para buscar el nombre del archivo .pdb asociado al archivo objeto:

1. Extraer un archivo de objeto de la biblioteca con [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.

1. Compruebe la ruta de acceso al archivo .pdb con **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.

También puede compilar con [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), por lo que no necesita el archivo pdb para utilizarse o quite el [/DEBUG](../../build/reference/debug-generate-debug-info.md) del vinculador si no tiene archivos .pdb para los objetos que se está vinculando.