---
title: Compilador advertencia (nivel 4) C4235 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4235
dev_langs: C++
helpviewer_keywords: C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0fea028932a48b9c7ee1a677a3e6dc8078edc35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4235"></a>Advertencia del compilador (nivel 4) C4235
se ha utilizado una extensión no estándar : la palabra clave 'palabra clave' no se admite en esta arquitectura  
  
 El compilador aún no admite la palabra clave utilizada.  
  
 Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, utilice [#pragma warning](../../preprocessor/warning.md). Por ejemplo, para convertir C4235 en una advertencia de nivel 2, utilice la siguiente línea de código  
  
```  
#pragma warning(2:4235)  
```  
  
 en el archivo de código fuente.