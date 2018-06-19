---
title: Error irrecuperable C1852 | Documentos de Microsoft
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
ms.openlocfilehash: d11160eea5e978a0c1ef67255d4e96b48fe2d101
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199516"
---
# <a name="fatal-error-c1852"></a>Error irrecuperable C1852
'filename' no es un archivo de encabezado precompilado válido  
  
 El archivo no es un encabezado precompilado.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Archivo no válido especificado con **/Yu** o **#pragma hdrstop**.  
  
2.  El compilador supone una extensión de archivo .pch si no se especifica lo contrario.