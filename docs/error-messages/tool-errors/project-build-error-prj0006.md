---
title: Error PRJ0006 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192788"
---
# <a name="project-build-error-prj0006"></a>Error PRJ0006 al compilar el proyecto

No se pudo abrir el archivo temporal ' file '. Asegúrese de que el archivo existe y de que el directorio no está protegido contra escritura.

Visual C++ no pudo crear un archivo temporal durante el proceso de compilación. Las razones para esto incluyen:

- No hay ningún directorio Temp.

- Directorio Temp de solo lectura.

- Espacio insuficiente en disco.

- La carpeta $ (IntDir) es de solo lectura o contiene archivos temporales que son de solo lectura.

Este error también se producirá después del error PRJ0007: no se pudo crear el directorio de salida ' directorio '. El error PRJ0007 significa que no se pudo crear el directorio $ (IntDir), lo que implica que la creación de archivos temporales también producirá un error.

Los archivos temporales se crean cada vez que se especifica:

- Un archivo de respuesta.

- Un paso de compilación personalizado.

- Un evento de compilación.
