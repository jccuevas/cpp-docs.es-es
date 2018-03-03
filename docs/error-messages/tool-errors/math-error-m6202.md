---
title: "Error matemático M6202 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 70a9496a2466ee36fed6d9c16194eef3516147f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6202"></a>Error matemático M6202
'función': error  
  
 Un argumento a la función especificada no era un valor de singularidad para esta función. La función no está definida para ese argumento.  
  
 Este error invoca la `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el control de algunos errores matemáticos de punto flotante de tiempo de ejecución.