---
title: Error irrecuperable C1099 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1099
dev_langs:
- C++
helpviewer_keywords:
- C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d97bed1bdc81c738ff20bb85038153181ddb06ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198786"
---
# <a name="fatal-error-c1099"></a>Error irrecuperable C1099
El motor de la función Editar y continuar está deteniendo la compilación  
  
 Editar y continuar cargó un archivo de encabezado precompilado al preparar la compilación de cambios en el código, pero las acciones posteriores (como los cambios en el código antes de la instrucción `#include` del encabezado precompilado o la detención del depurador) impidieron que Editar y continuar finalizase la compilación con ese proceso. No es necesario realizar ninguna acción para corregir este error.