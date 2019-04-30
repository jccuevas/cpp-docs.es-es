---
title: Error grave de NMAKE U1051
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: ddf1d262fb8dfc6e63b0bf5cc098b7b140539310
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367205"
---
# <a name="nmake-fatal-error-u1051"></a>Error grave de NMAKE U1051

No hay memoria suficiente

NMAKE se quedó sin memoria, incluida la memoria virtual, porque el archivo MAKE era demasiado grande o compleja.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Libere espacio en disco.

1. Aumentar el tamaño del archivo de paginación de Windows NT o el archivo de intercambio de Windows.

1. Si solo se utiliza la parte del archivo MAKE, divida el archivo MAKE en archivos independientes o usar **! IF** preprocesar directivas para limitar la cantidad que debe procesar NMAKE. El **! IF** directivas incluyen **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! ELSE** `IFDEF`, y **! ELSE** `IFNDEF`.