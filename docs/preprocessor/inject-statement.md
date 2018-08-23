---
title: inject_statement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4142b742ae6c2a758c2a2fb5e09c604959433f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539277"
---
# <a name="injectstatement"></a>inject_statement
**Específicos de C++**  
  
Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inject_statement("source_text")  
```  
  
### <a name="parameters"></a>Parámetros  
*source_text*  
Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.  
  
## <a name="remarks"></a>Comentarios  
 
El texto se coloca al principio de la declaración de espacio de nombres que incluye el contenido de la biblioteca de tipos en el archivo de encabezado.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)