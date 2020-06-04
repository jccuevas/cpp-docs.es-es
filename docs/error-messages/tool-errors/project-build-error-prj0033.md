---
title: Error PRJ0033 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: 141355ac49ec4722e85b5d4c25240e8048a72c9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192202"
---
# <a name="project-build-error-prj0033"></a>Error PRJ0033 al compilar el proyecto

La propiedad ' dependencias adicionales ' del paso de compilación personalizada para el archivo ' archivo ' contiene ' macro ' que se evalúa como ' macro_expansion '.

Un paso de compilación personalizado en un archivo contenía un error en su dependencia adicional probablemente debido a un problema de evaluación de macros. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de la ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio del proyecto.
