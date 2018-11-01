---
title: Error PRJ0006 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451564"
---
# <a name="project-build-error-prj0006"></a>Error PRJ0006 al compilar el proyecto

No se pudo abrir el archivo temporal 'file'. Asegúrese de que el archivo existe y que el directorio no está protegido contra escritura.

Visual C++ no se pudo crear un archivo temporal durante el proceso de compilación. Razones para esto incluyen:

- Ningún directorio temporal.

- Directorio temporal de solo lectura.

- Espacio en disco.

- La carpeta $ (IntDir) es de solo lectura o contiene archivos temporales que son de solo lectura.

Este error también se producirá tras error PRJ0007: no se pudo crear el directorio de resultados 'directorio'. Error PRJ0007 al significa que no se pudo crear el directorio $ (IntDir), lo que implica la creación de archivos temporalmente también producirá un error.

Archivos temporales se crean siempre que especifique:

- Un archivo de respuesta.

- Un paso de compilación personalizada.

- Un evento de compilación.