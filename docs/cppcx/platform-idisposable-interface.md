---
title: IDisposable (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3899c25d71ad08cc058280271080c19d11222ed
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589791"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable (Interfaz)
Se utiliza para liberar recursos no administrados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>Atributos  
 **GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
 **VersionAttribute**(NTDDI_WIN8)  
  
### <a name="members"></a>Miembros  
 La interfaz IDisposable hereda de la interfaz IUnknown. IDisposable también tiene los siguientes tipos de miembros:  
  
 **Métodos**  
  
 La interfaz IDisposable tiene los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|Desechar|Se utiliza para liberar recursos no administrados.|  
  
### <a name="requirements"></a>Requisitos  
 **Cliente mínimo admitido:** Windows 8  
  
 **Servidor mínimo admitido:** Windows Server 2012  
  
 **Espacio de nombres:** Plataforma