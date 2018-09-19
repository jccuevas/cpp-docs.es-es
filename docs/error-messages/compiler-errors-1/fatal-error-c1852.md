---
title: Error irrecuperable C1852 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1852
dev_langs:
- C++
helpviewer_keywords:
- C1852
ms.assetid: fa011004-b8d6-46f1-ba80-4785e4ce137f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0adfa7eed25f1902300fa2378b8ffc19eb8dfafd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023805"
---
# <a name="fatal-error-c1852"></a>Error irrecuperable C1852

'filename' no es un archivo de encabezado precompilado válido

El archivo no es un encabezado precompilado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Archivo no válido especificado con **/Yu** o **#pragma hdrstop**.

1. El compilador supone una extensión de archivo .pch si no se especifica lo contrario.