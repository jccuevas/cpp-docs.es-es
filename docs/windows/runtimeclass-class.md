---
title: RuntimeClass (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5c75492b55cd1c238798d3500e2157738c3c58f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass (Clase)
Representa una clase WinRT o COM que hereda las interfaces especificadas y proporciona el especificado en tiempo de ejecución de Windows, COM clásico y soporte técnico de referencia débil.  
  
Esta clase proporciona la implementación de código reutilizable de clases de WinRT y COM, que proporciona la implementación de `QueryInterface`, `AddRef`, `Release` etc., administra el recuento de referencias del módulo y tiene compatibilidad para proporcionar el generador de clases para objetos activables.
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
#### <a name="parameters"></a>Parámetros  
 `classFlags`  
Parámetro opcional. Una combinación de uno o varios [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) valores de enumeración. El `__WRL_CONFIGURATION_LEGACY__` macros se pueden definir para cambiar el valor predeterminado de classFlags para todas las clases en tiempo de ejecución en el proyecto. Si ha definido, RuntimeClass instancias son no ágiles de forma predeterminada. Cuando no está definido, las instancias de RuntimeClass son ágiles de forma predeterminada. Para evitar la ambigüedad especifique siempre el Microsoft::WRL::FtmBase en `TInterfaces` o RuntimeClassType::InhibitFtmBase. Tenga en cuenta que si InhibitFtmBase y FtmBase son que ambos usan el objeto será ágil.
 
 `TInterfaces`  
La lista de interfaces que implementa el objeto más allá de IUnknown, IInspectable u otras interfaces controlados por [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). También puede enumerar otras clases que se deriva, en particular Microsoft::WRL::FtmBase para hacer que el objeto agile y hacer que implementar IMarshal.
  
## <a name="members"></a>Miembros  
`RuntimeClassInitialize`Una función que inicializa el objeto si la función de plantilla MakeAndInitialize se utiliza para construir el objeto. Devuelve S_OK si el objeto se inicializó correctamente o un código de error COM si no se pudo inicializar. El código de error COM se propaga como el valor devuelto de MakeAndInitialize. Tenga en cuenta que no se llama al método RuntimeClassInitialize si la función de plantilla Asegúrese de que se utiliza para construir el objeto.

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
