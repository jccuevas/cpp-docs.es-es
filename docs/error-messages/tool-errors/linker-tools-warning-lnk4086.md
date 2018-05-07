---
title: Las herramientas del vinculador LNK4086 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7b3ad3a8ceebf97ccdcf7a1d8079886f54a3984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4086"></a>Advertencia de las herramientas del vinculador LNK4086
punto de entrada 'function' no es __stdcall con 'número' bytes de argumentos; no puede ejecutar la imagen  
  
 Debe ser el punto de entrada para un archivo DLL `__stdcall`. Vuelva a compilar la función con el [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) opción o especificar `__stdcall` o WINAPI al definir la función.