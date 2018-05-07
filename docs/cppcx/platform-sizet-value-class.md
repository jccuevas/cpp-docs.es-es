---
title: 'Clase de valor Platform:: sizet | Documentos de Microsoft'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c69bf34a7965c098f6a656907071e0899b785b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="platformsizet-value-class"></a>Platform::SizeT (Clase de valor)
Representa el tamaño de un objeto. SizeT es un tipo de datos sin signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public ref class SizeT sealed : ValueType  
```  
  
### <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|[SizeT::SizeT (Constructor)](#ctor)|Inicializa una nueva instancia de la clase con el valor especificado.|  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma  
  
 **Metadatos:** platform.winmd  

 ## <a name="ctor"></a>  Constructor de Sizet
Inicializa una nueva instancia de SizeT con el valor especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
SizeT( uint32 value1 );   SizeT( void* value2 );  
```  
  
### <a name="parameters"></a>Parámetros  
 value1  
 Un valor sin signo de 32 bits.  
  
 value2  
 Puntero a un valor sin signo de 32 bits.  
  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)