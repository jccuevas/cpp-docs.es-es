---
title: Clase de contenedor::swap | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62acdf7bf8278dfba3cf85bc9d5ced26a0f3fcea
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="container-classswap"></a>Clase de contenedor::swap
> [!NOTE]
>  Este tema se incluye en la documentación de Visual C++ como un ejemplo no funcional de los contenedores usados en la biblioteca estándar de C++. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../standard-library/stl-containers.md).  
  
Intercambia las secuencias controladas entre **\*this** y su argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void swap(Container& right);
```  
  
## <a name="remarks"></a>Comentarios  
Si **\*this.get\_allocator ==** _right_**.get_allocator**, realiza un intercambio en tiempo constante. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.  
  
## <a name="see-also"></a>Vea también  
[Sample Container (Clase)](../standard-library/sample-container-class.md)
