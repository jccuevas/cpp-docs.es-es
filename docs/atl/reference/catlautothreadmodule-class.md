---
title: Clase CAtlAutoThreadModule
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: f4bd1071380bf3e31c69c593c5db81112fdf21de
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168311"
---
# <a name="catlautothreadmodule-class"></a>Clase CAtlAutoThreadModule

Esta clase implementa un servidor COM de modelo de apartamento y agrupado de subprocesos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Observaciones

`CAtlAutoThreadModule`se deriva de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) e implementa un servidor com de modelo de apartamento y agrupado de subprocesos. `CAtlAutoThreadModule`usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un apartamento para cada subproceso del módulo.

Debe utilizar la macro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases. A continuación, debe agregar una única instancia de una clase derivada `CAtlAutoThreadModuleT` de como `CAtlAutoThreadModule`. Por ejemplo:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Esta clase reemplaza la clase [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) obsoleta.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="see-also"></a>Consulte también

[Clase CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
