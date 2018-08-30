---
title: CComEnum (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56a6211ac26a31b1ec01fdd2ad0579e4d9b52038
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223392"
---
# <a name="ccomenum-class"></a>CComEnum (clase)
Esta clase define un objeto de enumerador COM basándose en una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>  
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
 T,
    Copy>,
 public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>Parámetros  
 *base*  
 Una interfaz de enumerador COM. Consulte [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) para obtener un ejemplo. 
  
 *piid*  
 Un puntero al identificador de interfaz de la interfaz de enumerador.  
  
 *T*  
 El tipo de elemento que expone la interfaz de enumerador.  
  
 *Copiar*  
 Un homogéneos [Copiar directiva clase](../../atl/atl-copy-policy-classes.md).  
  
 *ThreadModel*  
 El modelo de subprocesos de la clase. El valor predeterminado de este parámetro es el modelo de subprocesos de objetos globales utilizado en el proyecto.  
  
## <a name="remarks"></a>Comentarios  
 `CComEnum` define un objeto de enumerador COM basándose en una matriz. Esta clase es análoga a [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) que implementa un enumerador que se basa en un contenedor de la biblioteca estándar de C++. Pasos habituales para usar esta clase se describen a continuación. Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class"></a>Para usar esta clase:  
  
- **TypeDef** una especialización de esta clase.  
  
-   Use la **typedef** como el argumento de plantilla en una especialización de `CComObject`.  
  
-   Cree una instancia de la `CComObject` especialización.  
  
-   Inicializar el objeto de enumerador llamando [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).  
  
-   La interfaz de enumerador se devuelven al cliente.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
## <a name="example"></a>Ejemplo  
 El código que se muestra a continuación proporciona una función reutilizable para crear e inicializar un objeto de enumerador.  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 Esta función de plantilla puede utilizarse para implementar la `_NewEnum` propiedad de una interfaz de colección, como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 Este código crea un **typedef** para `CComEnum` que expone un vector de variantes a través de la `IEnumVariant` interfaz. El `CVariantArrayCollection` simplemente se especializa la clase `CreateEnumerator` para trabajar con objetos del enumerador de este tipo y pasa los argumentos necesarios.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [CComEnumImpl (clase)](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)
