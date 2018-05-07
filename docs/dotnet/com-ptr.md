---
title: 'com:: PTR | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr
dev_langs:
- C++
helpviewer_keywords:
- com::ptr
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3c4e3bb91e161f9176bcf6964fc843d4e4bd707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="comptr"></a>com::ptr
Un contenedor para un objeto COM que puede usarse como un miembro de una clase CLR. El contenedor también automatiza la administración de la duración del objeto COM, liberando referencias de propiedad en el objeto cuando se llama a su destructor. Análoga a [clase CComPtr](../atl/reference/ccomptr-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <msclr\com\ptr.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 [Clase com:: PTR](../dotnet/com-ptr-class.md) se define en el \<msclr\com\ptr.h > archivo.  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de compatibilidad de C++](../dotnet/cpp-support-library.md)