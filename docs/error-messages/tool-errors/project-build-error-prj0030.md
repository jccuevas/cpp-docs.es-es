---
title: Error PRJ0030 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811481"
---
# <a name="project-build-error-prj0030"></a>Error PRJ0030 al compilar el proyecto

Error de expansión de macro. Recursividad de evaluación superado 32 niveles para $(macro).

Este error se produce por recursividad en las macros. Por ejemplo, si establece la **directorio intermedio** propiedad (consulte [página de propiedades General (proyecto)](../../build/reference/general-property-page-project.md)) en $(IntDir), tendrá la recursividad.

Para resolver este error, no defina macros o propiedades en cuanto a las macros que se usan para definir.