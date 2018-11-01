---
title: Error PRJ0030 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 2a6cde4ca48acb9aadfe3109084483dbb554e1e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488080"
---
# <a name="project-build-error-prj0030"></a>Error PRJ0030 al compilar el proyecto

Error de expansión de macro. Recursividad de evaluación superado 32 niveles para $(macro).

Este error se produce por recursividad en las macros. Por ejemplo, si establece la **directorio intermedio** propiedad (consulte [página de propiedades General (proyecto)](../../ide/general-property-page-project.md)) en $(IntDir), tendrá la recursividad.

Para resolver este error, no defina macros o propiedades en cuanto a las macros que se usan para definir.