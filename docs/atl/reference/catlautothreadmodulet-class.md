---
title: Clase CAtlAutoThreadModuleT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 082214794b2caa66e8be1127c664e0ffec18a394
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlautothreadmodulet-class"></a>Clase CAtlAutoThreadModuleT
Esta clase proporciona métodos para implementar un servidor COM agrupadas por subproceso, el modelo de apartamento.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase que va a implementar el servidor COM.  
  
 `ThreadAllocator`  
 La clase de administrar la selección de subproceso. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 `dwWait`  
 Especifica el intervalo de tiempo de espera, en milisegundos. El valor predeterminado es INFINITE, lo que significa intervalo de tiempo de espera del método nunca transcurre.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Esta función estática dinámicamente calcula y devuelve el número máximo de subprocesos para el módulo ejecutable, en función del número de procesadores.|  
  
## <a name="remarks"></a>Comentarios  
 La clase [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) deriva `CAtlAutoThreadModuleT` a fin de implementar un servidor COM agrupadas por subproceso, el modelo de apartamento. Reemplaza la clase obsoleta [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Esta clase no debe usarse en un archivo DLL, como el valor predeterminado `dwWait` valor de infinito producirá un interbloqueo cuando se descarga el archivo DLL.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads  
 Esta función estática dinámicamente calcula y devuelve el número máximo de subprocesos para el módulo ejecutable, en función del número de procesadores.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de subprocesos que se creen en el módulo del archivo EXE.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea usar un método diferente para calcular el número de subprocesos. De forma predeterminada, el número de subprocesos se basa en el número de procesadores.  
  
## <a name="see-also"></a>Vea también  
 [Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)
