---
title: Error irrecuperable C1852
ms.date: 11/04/2016
f1_keywords:
- C1852
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
ms.openlocfilehash: 540febabc8f2947f11b58cf7eadee53d47f7bef3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202883"
---
# <a name="fatal-error-c1852"></a>Error irrecuperable C1852

'filename' no es un archivo de encabezado precompilado válido

El archivo no es un encabezado precompilado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Archivo no válido especificado con **/Yu** o **#pragma hdrstop**.

1. El compilador supone una extensión de archivo .pch si no se especifica lo contrario.
