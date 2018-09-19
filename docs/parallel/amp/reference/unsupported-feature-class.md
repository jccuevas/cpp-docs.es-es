---
title: unsupported_feature (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
dev_langs:
- C++
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7472e8fa8932983569ad9e2a9c1fe6cdfc9318b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059688"
---
# <a name="unsupportedfeature-class"></a>unsupported_feature (Clase)
La excepción que se produce cuando se usa una característica no compatible.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unsupported_feature (Constructor)](#ctor)|Crea una nueva instancia de la `unsupported_feature` excepción.|  

  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## <a name="unsupported_feature__ctor"></a> unsupported_feature) 

  Crea una nueva instancia de la excepción unsupported_feature.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
explicit unsupported_feature(  
    const char * _Message ) throw();  
  
unsupported_feature() throw();  
```  
  
### <a name="parameters"></a>Parámetros  
*_Cuerpo*<br/>
Descripción del error.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto `unsupported_feature`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
