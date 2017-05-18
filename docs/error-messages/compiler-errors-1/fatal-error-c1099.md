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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 74ef24f35084e76d6f8ad9d3eec3459e7f50a930
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1099"></a>Error irrecuperable C1099
El motor de la función Editar y continuar está deteniendo la compilación  
  
 Editar y continuar cargó un archivo de encabezado precompilado al preparar la compilación de cambios en el código, pero las acciones posteriores (como los cambios en el código antes de la instrucción `#include` del encabezado precompilado o la detención del depurador) impidieron que Editar y continuar finalizase la compilación con ese proceso. No es necesario realizar ninguna acción para corregir este error.
