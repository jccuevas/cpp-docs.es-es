---
title: Error irrecuperable C1099 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1099
dev_langs: C++
helpviewer_keywords: C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 928ced6fe9e283cf16db651ecbf6164164e3174e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1099"></a>Error irrecuperable C1099
El motor de la función Editar y continuar está deteniendo la compilación  
  
 Editar y continuar cargó un archivo de encabezado precompilado al preparar la compilación de cambios en el código, pero las acciones posteriores (como los cambios en el código antes de la instrucción `#include` del encabezado precompilado o la detención del depurador) impidieron que Editar y continuar finalizase la compilación con ese proceso. No es necesario realizar ninguna acción para corregir este error.