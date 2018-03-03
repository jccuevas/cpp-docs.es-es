---
title: Las herramientas del vinculador LNK1241 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb256607f6babbba90fbd17ae89bfbdfcfb48138
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1241"></a>Error de las herramientas del vinculador LNK1241
archivo de recursos 'archivo de recursos' ya se ha especificado  
  
 Este error se genera si ejecuta **cvtres** manualmente desde la línea de comandos y si, a continuación, pase el archivo .obj resultante de archivos al vinculador además a otros archivos. res.  
  
 Para especificar varios archivos. res, deben pasar todos al compilador como archivos .res, no desde los archivos .obj crean por **cvtres**.