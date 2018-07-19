---
title: Error matemático M6202 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4596b9782bc1de0e6ccd52bfcd03965415adb353
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332057"
---
# <a name="math-error-m6202"></a>Error matemático M6202
'función': error  
  
 Un argumento a la función especificada no era un valor de singularidad para esta función. La función no está definida para ese argumento.  
  
 Este error invoca la `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el control de algunos errores matemáticos de punto flotante de tiempo de ejecución.