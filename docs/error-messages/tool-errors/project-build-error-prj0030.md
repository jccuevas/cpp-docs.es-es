---
title: Error PRJ0030 al compilar el proyecto
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 3675c3796ae37df848e458aa2db665d8c4aa7766
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192515"
---
# <a name="project-build-error-prj0030"></a>Error PRJ0030 al compilar el proyecto

Error de expansión de macro. La recursividad de evaluación superó los 32 niveles para $ (macro).

Este error se debe a una recursividad en las macros. Por ejemplo, si establece la propiedad de **directorio intermedio** (vea [Página de propiedades general (proyecto)](../../build/reference/general-property-page-project.md)) en $ (IntDir), tendrá recursividad.

Para resolver este error, no defina macros ni propiedades en términos de macros que se usan para definir.
