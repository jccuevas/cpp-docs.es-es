---
title: high_method_prefix | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- high_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- high_method_prefix attribute
ms.assetid: cacebf09-12f5-4919-ad40-939e206e340c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e1326f2cd5d1984fefc360ea35f1a333e794407
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="highmethodprefix"></a>high_method_prefix
**C++ Specific**  
  
 Especifica un prefijo que se utilizará para designar propiedades y métodos de alto nivel.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
high_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Prefix`  
 Prefijo que se va a utilizar.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, las propiedades y los métodos de control de errores de alto nivel se exponen mediante funciones miembro denominadas sin prefijo. Los nombres son de la biblioteca de tipos.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)