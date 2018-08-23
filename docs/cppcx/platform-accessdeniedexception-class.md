---
title: Accessdeniedexception (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 808de08163f0f94e4c3d0064fced7cb81f83c931
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597941"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException (Clase)
Se produce cuando se deniega el acceso a un recurso o a una característica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
### <a name="remarks"></a>Comentarios  
 Si obtienes esta excepción, asegúrate de que has solicitado la capacidad adecuada y de que has realizado las declaraciones necesarias en el manifiesto del paquete de tu aplicación. Para obtener más información, consulta [COMException](../cppcx/platform-comexception-class.md) .  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd  
  
## <a name="see-also"></a>Vea también  
 [Platform::COMException (Clase)](../cppcx/platform-comexception-class.md)