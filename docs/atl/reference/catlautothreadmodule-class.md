---
title: CAtlAutoThreadModule (clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: acd277160bc277e919a2802541310aa55446e00c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619718"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule (clase)

Esta clase implementa un servidor COM de subprocesamiento de modelo, agrupadas por subproceso.

> [!IMPORTANT]
> Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Comentarios

`CAtlAutoThreadModule` se deriva de [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) e implementa un servidor COM de subprocesamiento de modelo, agrupadas por subproceso. `CAtlAutoThreadModule` usa [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un contenedor para cada subproceso en el módulo.

Debe usar el [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) macro en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de clases. A continuación, debe agregar una única instancia de una clase derivada de `CAtlAutoThreadModuleT` como `CAtlAutoThreadModule`. Por ejemplo:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Esta clase reemplaza el atributo obsolete [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[CAtlAutoThreadModuleT (clase)](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule (clase)](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
