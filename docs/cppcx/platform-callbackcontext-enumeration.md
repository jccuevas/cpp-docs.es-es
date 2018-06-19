---
title: Callbackcontext (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 757de5f686bb809a5d2fb159a3ee547a20edc982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086959"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext (Enumeración)
Especifica el contexto del subproceso en el que se ejecuta una función de devolución de llamada (controlador de eventos).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum class CallbackContext {};  
```  
  
### <a name="members"></a>Miembros  
  
|Código de tipo|Descripción|  
|---------------|-----------------|  
|Cualquiera|La función de devolución de llamada se puede ejecutar en cualquier contexto de subproceso.|  
|Igual|La función de devolución de llamada solo se puede ejecutar en el contexto de subproceso que inició la operación asincrónica.|  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd