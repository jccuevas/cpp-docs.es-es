---
title: RuntimeClass (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d777dd15e484ae296139bbe2bdc9b0cddcab2d59
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606337"
---
# <a name="runtimeclass-class"></a>RuntimeClass (Clase)
Representa una clase WinRT o COM que hereda las interfaces especificadas y proporciona el especificado en tiempo de ejecución de Windows, COM clásico y el soporte técnico de la referencia débil.  
  
Esta clase proporciona la implementación de código reutilizable de clases COM y WinRT, que proporciona la implementación de `QueryInterface`, `AddRef`, `Release` etc., administra el recuento de referencias del módulo y tiene compatibilidad para proporcionar el generador de clases para objetos activables.
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
### <a name="parameters"></a>Parámetros  
 *classFlags*  
Parámetro opcional. Una combinación de uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valores de enumeración. El `__WRL_CONFIGURATION_LEGACY__` macros se pueden definir para cambiar el valor predeterminado de classFlags para todas las clases en tiempo de ejecución en el proyecto. Si ha definido, RuntimeClass instancias son no ágiles de forma predeterminada. Cuando no está definido, las instancias de RuntimeClass son ágiles de forma predeterminada. Para evitar la ambigüedad especifique siempre el `Microsoft::WRL::FtmBase` en `TInterfaces` o `RuntimeClassType::InhibitFtmBase`. Tenga en cuenta que si InhibitFtmBase y FtmBase son que ambos utilizan el objeto será ágil.
 
 *TInterfaces*  
La lista de interfaces que el objeto implementa más allá de `IUnknown`, `IInspectable` u otras interfaces controlados por [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). También puede enumerar otras clases que se deriva, en particular `Microsoft::WRL::FtmBase` para hacer que el objeto agile y provocar que implemente `IMarshal`.
  
## <a name="members"></a>Miembros  
`RuntimeClassInitialize` Una función que inicializa el objeto si el `MakeAndInitialize` función de plantilla se usa para construir el objeto. Devuelve S_OK si el objeto se inicializó correctamente, o un código de error COM si no se pudo inicializar. El código de error COM se propaga como el valor devuelto de `MakeAndInitialize`. Tenga en cuenta que el `RuntimeClassInitialize` no se llama al método si el `Make` función de plantilla se usa para construir el objeto.

### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass (constructor)](../windows/runtimeclass-runtimeclass-constructor.md)|Inicializa la instancia actual de la clase RuntimeClass.|  
|[RuntimeClass::~RuntimeClass (destructor)](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Desinicializa la instancia actual de la clase RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
Se trata de un detalle de implementación.
  
## <a name="requirements"></a>Requisitos  
**Encabezado:** implements.h  
  
**Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)