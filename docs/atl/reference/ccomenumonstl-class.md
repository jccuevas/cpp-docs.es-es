---
title: CComEnumOnSTL (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c380ba7b6c2c13f178a15263e1ff510f9f3c31c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL (clase)
Esta clase define un objeto de enumerador COM basándose en una colección de la biblioteca estándar de C++.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>  
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
 T,
    Copy,
 CollType>,
    public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>Parámetros  
 `Base`  
 Un enumerador COM ( [interfaz IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfaz.  
  
 `piid`  
 Un puntero al identificador de interfaz de la interfaz de enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz de enumerador.  
  
 `Copy`  
 A [Copiar directiva](../../atl/atl-copy-policy-classes.md) clase.  
  
 `CollType`  
 Una clase de contenedor de la biblioteca estándar de C++.  
  
## <a name="remarks"></a>Comentarios  
 `CComEnumOnSTL` define un objeto de enumerador COM basándose en una colección de la biblioteca estándar de C++. Esta clase puede utilizarse por sí solo o en combinación con [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Pasos habituales para usar esta clase se describen a continuación. Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Para utilizar esta clase con ICollectionOnSTLImpl:  
  
- `typedef` una especialización de esta clase.  
  
-   Use la `typedef` como el argumento de plantilla final en una especialización de `ICollectionOnSTLImpl`.  
  
 Vea [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md) para obtener un ejemplo.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Para usar esta clase independientemente ICollectionOnSTLImpl:  
  
- `typedef` una especialización de esta clase.  
  
-   Use la `typedef` como el argumento de plantilla en una especialización de `CComObject`.  
  
-   Cree una instancia de la `CComObject` especialización.  
  
-   Inicializar el objeto de enumerador mediante una llamada a [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Devuelve la interfaz de enumerador para el cliente.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
## <a name="example"></a>Ejemplo  
 El código que se muestra a continuación muestra una función genérica para controlar la creación e inicialización de un objeto de enumerador:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Esta función de plantilla puede utilizarse para implementar la `_NewEnum` propiedad de una interfaz de colección, tal y como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Este código crea un `typedef` para `CComEnumOnSTL` que expone un vector de `CComVariant`s por medio de la **IEnumVariant** interfaz. El **CVariantCollection** clase simplemente especializa **CreateSTLEnumerator** para trabajar con objetos de enumerador de este tipo.  
  
## <a name="see-also"></a>Vea también  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Ejemplo de ATLCollections: Muestra ICollectionOnSTLImpl, CComEnumOnSTL y clases de directiva de copia personalizada](../../visual-cpp-samples.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl (clase)](../../atl/reference/ienumonstlimpl-class.md)
