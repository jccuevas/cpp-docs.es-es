---
title: Error grave de NMAKE U1051 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3d3a14b75a30aa22bcc9faafb97a218051bb080
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045021"
---
# <a name="nmake-fatal-error-u1051"></a>Error grave de NMAKE U1051

No hay memoria suficiente

NMAKE se quedó sin memoria, incluida la memoria virtual, porque el archivo MAKE era demasiado grande o compleja.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Libere espacio en disco.

1. Aumentar el tamaño del archivo de paginación de Windows NT o el archivo de intercambio de Windows.

1. Si solo se utiliza la parte del archivo MAKE, divida el archivo MAKE en archivos independientes o usar **! IF** preprocesar directivas para limitar la cantidad que debe procesar NMAKE. El **! IF** directivas incluyen **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! ELSE** `IFDEF`, y **! ELSE** `IFNDEF`.