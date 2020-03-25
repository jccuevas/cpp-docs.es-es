---
title: Error PRJ0034 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: bcb7e22d6a09e3435eb2236532101a1836c08a03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192200"
---
# <a name="project-build-error-prj0034"></a>Error PRJ0034 al compilar el proyecto

La propiedad ' dependencias adicionales ' del paso de compilación personalizada del nivel de proyecto contenía ' macro ' que se evalúa como ' macro_expansion '.

Un paso de compilación personalizado en un proyecto contenía un error en su dependencia adicional probablemente debido a un problema de evaluación de macros. Este error también puede significar que la ruta de acceso tiene un formato incorrecto, que contiene caracteres o combinaciones de caracteres que no son válidos en una ruta de acceso de archivo.

Para resolver este error, corrija la macro o corrija la especificación de la ruta de acceso. La ruta de acceso evaluada es una ruta de acceso absoluta del directorio del proyecto.
