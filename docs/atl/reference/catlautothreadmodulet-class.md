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
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 86b35f0a6a3ab43c170ee710838ec9ba0e2fc5b0
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="catlautothreadmodulet-class"></a>Clase CAtlAutoThreadModuleT
Esta clase proporciona métodos para implementar un servidor COM de subprocesamiento de modelo, agrupadas por el subproceso.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase que implementará el servidor COM.  
  
 `ThreadAllocator`  
 La clase de administración de selección de subproceso. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 `dwWait`  
 Especifica el intervalo de tiempo de espera, en milisegundos. El valor predeterminado es INFINITE, lo que significa intervalo de tiempo de espera del método nunca transcurre.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Esta función estática dinámicamente calcula y devuelve el número máximo de subprocesos para el módulo EXE, en función del número de procesadores.|  
  
## <a name="remarks"></a>Comentarios  
 La clase [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) se deriva de `CAtlAutoThreadModuleT` para implementar un servidor COM de subprocesamiento de modelo, agrupadas por el subproceso. Reemplaza la clase obsoleta [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Esta clase no debería utilizarse en un archivo DLL, como el valor predeterminado `dwWait` valor de infinito producirá un interbloqueo cuando se descarga el archivo DLL.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads  
 Esta función estática dinámicamente calcula y devuelve el número máximo de subprocesos para el módulo EXE, en función del número de procesadores.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de subprocesos que se creará en el módulo del archivo EXE.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea utilizar un método diferente para calcular el número de subprocesos. De forma predeterminada, el número de subprocesos se basa en el número de procesadores.  
  
## <a name="see-also"></a>Vea también  
 [Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)

