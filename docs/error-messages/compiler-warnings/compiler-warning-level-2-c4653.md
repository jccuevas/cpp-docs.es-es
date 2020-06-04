---
title: Advertencia del compilador (nivel 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161742"
---
# <a name="compiler-warning-level-2-c4653"></a>Advertencia del compilador (nivel 2) C4653

opción del compilador ' opción ' incoherente con el encabezado precompilado; se omitió la opción de línea de comandos actual

Una opción especificada con la opción usar encabezados precompilados ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) era incoherente con las opciones especificadas cuando se creó el encabezado precompilado. Esta compilación usó la opción especificada cuando se creó el encabezado precompilado.

Esta advertencia puede producirse cuando se ha especificado un valor diferente para la opción de estructuras del paquete ([/ZP](../../build/reference/zp-struct-member-alignment.md)) durante la compilación del encabezado precompilado.
