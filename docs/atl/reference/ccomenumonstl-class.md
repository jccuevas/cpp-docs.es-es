---
title: CComEnumOnSTL (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: 21
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
ms.openlocfilehash: 23e234f82ce8c77a6ebde50070475deeab59f362
ms.lasthandoff: 02/24/2017

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
 El tipo de elemento que expone la interfaz de enumerador.  
  
 `Copy`  
 Un [Copiar directiva](../../atl/atl-copy-policy-classes.md) clase.  
  
 `CollType`  
 Una clase de contenedor de la biblioteca estándar de C++.  
  
## <a name="remarks"></a>Comentarios  
 `CComEnumOnSTL`define un objeto de enumerador COM basándose en una colección de la biblioteca estándar de C++. Esta clase se puede utilizar por sí solo o en combinación con [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Los pasos típicos para utilizar esta clase se describen a continuación. Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Para utilizar esta clase con ICollectionOnSTLImpl:  
  
- `typedef`una especialización de esta clase.  
  
-   Utilice la `typedef` como argumento de una especialización de plantilla final `ICollectionOnSTLImpl`.  
  
 Consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md) para obtener un ejemplo.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Para utilizar esta clase independientemente de ICollectionOnSTLImpl:  
  
- `typedef`una especialización de esta clase.  
  
-   Utilice la `typedef` como argumento de plantilla en la especialización de `CComObject`.  
  
-   Cree una instancia de la `CComObject` especialización.  
  
-   Inicializar el objeto de enumerador llamando a [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   La interfaz de enumerador se devuelven al cliente.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h  
  
## <a name="example"></a>Ejemplo  
 El código siguiente proporciona una función para controlar la creación e inicialización de un objeto de enumerador genérica:  
  
 [!code-cpp[NVC_ATL_COM&#34;](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Esta función de plantilla puede utilizarse para implementar la `_NewEnum` propiedad de una interfaz de colección, como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM&#35;](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Este código crea un `typedef` de `CComEnumOnSTL` que expone un vector de `CComVariant`s por medio de la **IEnumVariant** interfaz. El **CVariantCollection** clase simplemente especializa **CreateSTLEnumerator** para trabajar con objetos del enumerador de este tipo.  
  
## <a name="see-also"></a>Vea también  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Ejemplo ATLCollections: Muestra ICollectionOnSTLImpl, CComEnumOnSTL y clases de directivas de copia personalizadas](../../visual-cpp-samples.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Clase IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

