---
title: TLBID | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tlbid
dev_langs: C++
helpviewer_keywords: tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 812b105fc02782b611b3f55061e448062dcd07c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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