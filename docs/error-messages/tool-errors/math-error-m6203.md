---
title: "Error matemático M6203 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6203
dev_langs: C++
helpviewer_keywords: M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f65e016a736113ea4bcb9e488e792daa673d00d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6203"></a>Error matemático M6203
'función': error _OVERFLOW  
  
 El resultado de la función especificada era demasiado grande para representarse.  
  
 Este error invoca la `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el control de algunos errores matemáticos de punto flotante de tiempo de ejecución.