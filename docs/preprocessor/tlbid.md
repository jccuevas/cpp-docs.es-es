---
title: TLBID | Microsoft Docs
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
ms.openlocfilehash: f5bd922089bcf189c403a97679a593a985603a12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446262"
---
# <a name="tlbid"></a>tlbid
**Específicos de C++**  
  
Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
tlbid(number)  
```  
  
### <a name="parameters"></a>Parámetros  
*Número*  
Número de la biblioteca de tipos en `filename`.  
  
## <a name="remarks"></a>Comentarios  
 
Si se crean varias bibliotecas de tipos en un único archivo DLL, se pueden cargar bibliotecas distintas de la biblioteca de tipos principal mediante el uso de **tlbid**.  
  
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
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)