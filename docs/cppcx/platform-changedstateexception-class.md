---
title: Changedstateexception (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
dev_langs:
- C++
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0910500c24a4e7ca574ac2eebc6264148d14a410
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException (Clase)
Se produce cuando el estado interno de un objeto ha cambiado, invalidando de este modo los resultados del método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Comentarios  
 Un ejemplo donde se produce esta excepción es cuando los métodos de un iterador de colección o de una vista de colección se invocan después de que la colección principal haya cambiado, invalidando los resultados del método.  
  
 Para obtener más información, consulta la clase [COMException](../cppcx/platform-comexception-class.md) .  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd  
  
## <a name="see-also"></a>Vea también  
 [Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)