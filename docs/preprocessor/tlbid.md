---
title: TLBID | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d651546733f42b1a714ac7a39992fa2d392c8fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839873"
---
# <a name="tlbid"></a>tlbid
**Específicos de C++**  
  
 Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
tlbid(number)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `number`  
 Número de la biblioteca de tipos en `filename`.  
  
## <a name="remarks"></a>Comentarios  
 Si hay varias bibliotecas de tipos compiladas en un mismo archivo DLL, se pueden cargar bibliotecas distintas de la biblioteca de tipos principal mediante `tlbid`.  
  
 Por ejemplo:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 equivale a:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)