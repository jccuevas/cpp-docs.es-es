---
title: Error del compilador de recursos RC2147
ms.date: 11/04/2016
f1_keywords:
- RC2147
helpviewer_keywords:
- RC2147
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
ms.openlocfilehash: f76c61ace4e0e1d8eea9a33669b66021861c36f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191150"
---
# <a name="resource-compiler-error-rc2147"></a>Error del compilador de recursos RC2147

IDENTIFICADOR de subidioma no es un número

El valor del identificador de subidioma debe ser un número.

La instrucción **LANGUAGE** debe usar la sintaxis siguiente:

**LANGUAGE** *Primary_language_ID*de idioma,*secondary_language_ID*

Los identificadores de subidioma válidos se definen como **SUBLANG_** constantes en el archivo winnt. h.
