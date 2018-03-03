---
title: Variables globales de ATL | Documentos de Microsoft
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcf9a88e57d351a3fb6647f6deea3eccbad33bf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-global-variables"></a>Variables globales de ATL

## <a name="patlmodule"></a>_pAtlModule  
Una variable global que lo almacena un puntero al módulo actual.  

```cpp  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
### <a name="remarks"></a>Comentarios  
Métodos en esta variable global pueden utilizarse para proporcionar la funcionalidad que proporciona la clase CComModule (ya obsoleta) en Visual C++ 6.0.

### <a name="example"></a>Ejemplo  

```cpp  
LONG lLocks = _pAtlModule->GetLockCount();  
```  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  

