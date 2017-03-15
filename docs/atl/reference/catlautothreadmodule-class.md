---
title: Clase de CAtlAutoThreadModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlAutoThreadModule
- CAtlAutoThreadModule
- ATL::CAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 09f4a7061ce1e4a09d0d27bd90dfcc16a37f4d5b
ms.lasthandoff: 02/24/2017

---
# <a name="catlautothreadmodule-class"></a>Clase de CAtlAutoThreadModule
Esta clase implementa un servidor COM de subprocesamiento de modelo, agrupadas por el subproceso.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>Comentarios  
 `CAtlAutoThreadModule`se deriva de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) e implementa un servidor COM de subprocesamiento de modelo, agrupadas por el subproceso. `CAtlAutoThreadModule`usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un contenedor para cada subproceso en el módulo.  
  
 Debe utilizar el [DECLARE_CLASSFACTORY_AUTO_THREAD](http://msdn.microsoft.com/library/19d7105e-03e8-4412-9f5e-5384c8a5e18f) macro en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases. A continuación, debe agregar una única instancia de una clase derivada de `CAtlAutoThreadModuleT` como `CAtlAutoThreadModule`. Por ejemplo:  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  Esta clase reemplaza la obsoleta [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)   
 [Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)
