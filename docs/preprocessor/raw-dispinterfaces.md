---
title: raw_dispinterfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 093c994de24b947c53bfc19d33213e77f3ec2593
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541285"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Específicos de C++**  
  
Indica al compilador que genere funciones de contenedor de bajo nivel para dispinterface métodos y propiedades que llaman a `IDispatch::Invoke` y devolver el código de error HRESULT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Comentarios  
 
Si no se especifica este atributo, solo se generan los contenedores de alto nivel, que inician excepciones de C++ en caso de error.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)