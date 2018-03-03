---
title: Clase CComEnum | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 792c5ff95858936d38d9a87350dd3ca405c5ec66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomenum-class"></a>Clase CComEnum
Esta clase define un objeto de enumerador de COM basado en una matriz.  
  
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
 `Base`  
 Un enumerador COM ( [interfaz IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfaz.  
  
 `piid`  
 Un puntero al identificador de interfaz de la interfaz de enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz de enumerador.  
  
 `Copy`  
 Un homogéneos [copiar clase directiva](../../atl/atl-copy-policy-classes.md).  
  
 `ThreadModel`  
 El modelo de subprocesos de la clase. El valor predeterminado de este parámetro es el modelo de subprocesos de objetos globales utilizado en el proyecto.  
  
## <a name="remarks"></a>Comentarios  
 `CComEnum`define un objeto de enumerador COM basado en una matriz. Esta clase es análoga a [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) que implementa un enumerador que se basa en un contenedor de la biblioteca estándar de C++. Pasos habituales para usar esta clase se describen a continuación. Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class"></a>Para utilizar esta clase:  
  
- `typedef`una especialización de esta clase.  
  
-   Use la `typedef` como el argumento de plantilla en una especialización de `CComObject`.  
  
-   Cree una instancia de la `CComObject` especialización.  
  
-   Inicializar el objeto de enumerador mediante una llamada a [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).  
  
-   Devuelve la interfaz de enumerador para el cliente.  
  
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
  
 Esta función de plantilla puede utilizarse para implementar la `_NewEnum` propiedad de una interfaz de colección, tal y como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 Este código crea un `typedef` para `CComEnum` que expone un vector de **VARIANT**s a través de la **IEnumVariant** interfaz. El **CVariantArrayCollection** clase simplemente especializa **CreateEnumerator** para trabajar con objetos de enumerador de este tipo y pasa los argumentos necesarios.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Clase CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)
