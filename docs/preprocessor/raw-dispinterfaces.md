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
ms.openlocfilehash: 02133e6b9d884fa8e0a175dd01845035ec8b96a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435953"
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
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)