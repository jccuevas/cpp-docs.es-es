---
title: Error del compilador de recursos RC2148
ms.date: 11/04/2016
f1_keywords:
- RC2148
helpviewer_keywords:
- RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
ms.openlocfilehash: e2394dbb93dd2d203d65760d805e09f60a692ba4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191332"
---
# <a name="resource-compiler-error-rc2148"></a>Error del compilador de recursos RC2148

IDENTIFICADOR de subidioma demasiado grande

El valor del identificador de subidioma estaba fuera del intervalo.

La instrucción **LANGUAGE** debe usar la sintaxis siguiente:

**LANGUAGE** *Primary_language_ID*de idioma,*secondary_language_ID*

Los identificadores de subidioma válidos se definen como **SUBLANG_** constantes en el archivo winnt. h.
