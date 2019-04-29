---
title: Error PRJ0006 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: d62c774411fda80a3e94044b3272567177328ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359662"
---
# <a name="project-build-error-prj0006"></a>Error PRJ0006 al compilar el proyecto

No se pudo abrir el archivo temporal 'file'. Asegúrese de que el archivo existe y que el directorio no está protegido contra escritura.

Visual C++ no se pudo crear un archivo temporal durante el proceso de compilación. Razones para esto incluyen:

- Ningún directorio temporal.

- Directorio temporal de solo lectura.

- Espacio en disco.

- La carpeta $ (IntDir) es de solo lectura o contiene archivos temporales que son de solo lectura.

Este error también se producirá error PRJ0007 a las siguientes: No se pudo crear el directorio de resultados 'directorio'. Error PRJ0007 al significa que no se pudo crear el directorio $ (IntDir), lo que implica la creación de archivos temporalmente también producirá un error.

Archivos temporales se crean siempre que especifique:

- Un archivo de respuesta.

- Un paso de compilación personalizada.

- Un evento de compilación.