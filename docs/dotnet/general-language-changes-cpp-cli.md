---
title: Cambios del lenguaje general (C++ / CLI) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87ff7f55b67c4e8a84d15099432962ee0939d13a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="general-language-changes-ccli"></a>Cambios generales en el lenguaje (C++/CLI)
Un número de características del lenguaje CLR ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 Los cambios descritos en esta sección son una especie de Miscelánea del lenguaje. Incluye un cambio en el control de literales de cadena, un cambio en la resolución de sobrecarga entre los puntos suspensivos y la `Param` de atributo, el cambio de `typeof` a `typeid`, un cambio en el que realiza la llamada de listas de inicializadores de constructor y la Introducción de una nueva notación de conversión de `safe_cast`.  
  
 [Literal de cadena](../dotnet/string-literal.md)  
 Describe cómo ha cambiado el control de literales de cadena.  
  
 [Matriz de parámetros y puntos suspensivos](../dotnet/param-array-and-ellipsis.md)  
 Describe cómo `ParamArray` ahora tiene prioridad sobre los puntos suspensivos (`...`) para resolver las llamadas de función con un número variable de argumentos.  
  
 [T::typeid reemplaza a typeof](../dotnet/typeof-goes-to-t-typeid.md)  
 Describe cómo el `typeof` ha suplantado al operador `typeid`.  
  
 [Listas de inicializadores](../dotnet/initializer-lists.md)  
 Trata sobre los cambios en el orden de llamada de listas de inicializadores.  
  
 [Notación de conversión e introducción de safe_cast<>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 Se describen los cambios realizados a la notación de conversión y, en particular la introducción de `safe_cast`.  
  
## <a name="see-also"></a>Vea también  
 [Manual de migraciones C++/CLI](../dotnet/cpp-cli-migration-primer.md)