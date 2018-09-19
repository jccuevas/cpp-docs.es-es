---
title: Error PRJ0030 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964fedd40f577a8b337c4ad0c20ba80d33ed2a23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099927"
---
# <a name="project-build-error-prj0030"></a>Error PRJ0030 al compilar el proyecto

Error de expansión de macro. Recursividad de evaluación superado 32 niveles para $(macro).

Este error se produce por recursividad en las macros. Por ejemplo, si establece la **directorio intermedio** propiedad (consulte [página de propiedades General (proyecto)](../../ide/general-property-page-project.md)) en $(IntDir), tendrá la recursividad.

Para resolver este error, no defina macros o propiedades en cuanto a las macros que se usan para definir.