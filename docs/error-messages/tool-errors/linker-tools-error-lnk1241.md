---
title: Las herramientas del vinculador LNK1241 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b02b1d9d06706c70478d958dd3c2af8dbc9c2c03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299180"
---
# <a name="linker-tools-error-lnk1241"></a>Error de las herramientas del vinculador LNK1241
archivo de recursos 'archivo de recursos' ya se ha especificado  
  
 Este error se genera si ejecuta **cvtres** manualmente desde la línea de comandos y si, a continuación, pase el archivo .obj resultante de archivos al vinculador además a otros archivos. res.  
  
 Para especificar varios archivos. res, deben pasar todos al compilador como archivos .res, no desde los archivos .obj crean por **cvtres**.