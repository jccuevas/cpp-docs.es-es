---
title: Error irrecuperable C1099 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1099
dev_langs:
- C++
helpviewer_keywords:
- C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 496ffdb68cb1cbb3023319ab3324a52bb1d9db9e
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1099"></a>Error irrecuperable C1099
El motor de la función Editar y continuar está deteniendo la compilación  
  
 Editar y continuar cargó un archivo de encabezado precompilado al preparar la compilación de cambios en el código, pero las acciones posteriores (como los cambios en el código antes de la instrucción `#include` del encabezado precompilado o la detención del depurador) impidieron que Editar y continuar finalizase la compilación con ese proceso. No es necesario realizar ninguna acción para corregir este error.
