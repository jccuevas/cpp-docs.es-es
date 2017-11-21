---
title: Las herramientas del vinculador LNK4086 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4086
dev_langs: C++
helpviewer_keywords: LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 85965c09bdbdff3ec271d2e1c5ef1913650009c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4086"></a>Advertencia de las herramientas del vinculador LNK4086
punto de entrada 'function' no es __stdcall con 'número' bytes de argumentos; no puede ejecutar la imagen  
  
 Debe ser el punto de entrada para un archivo DLL `__stdcall`. Vuelva a compilar la función con el [/Gz](../../build/reference/gd-gr-gv-gz-calling-convention.md) opción o especificar `__stdcall` o WINAPI al definir la función.