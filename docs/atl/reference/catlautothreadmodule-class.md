---
title: Clase de CAtlAutoThreadModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
dev_langs: C++
helpviewer_keywords: CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ceff548fe53ff317eaca432a5e0c223cdc0a4e6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="catlautothreadmodule-class"></a>Clase de CAtlAutoThreadModule
Esta clase implementa un servidor COM agrupadas por subproceso, el modelo de apartamento.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```  
  
## <a name="remarks"></a>Comentarios  
 `CAtlAutoThreadModule`se deriva de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) e implementa un servidor COM agrupadas por subproceso, el modelo de apartamento. `CAtlAutoThreadModule`usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un contenedor para cada subproceso en el módulo.  
  
 Debe utilizar el [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases. A continuación, debe agregar una única instancia de una clase derivada de `CAtlAutoThreadModuleT` como `CAtlAutoThreadModule`. Por ejemplo:  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  Esta clase reemplaza el atributo obsolete [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)   
 [Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)
