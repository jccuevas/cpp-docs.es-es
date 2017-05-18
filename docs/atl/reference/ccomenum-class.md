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
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 72c172d7a619bb4fd1bd265e465653b691c0bc7b
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomenum-class"></a>Clase CComEnum
Esta clase define un objeto de enumerador COM basado en una matriz.  
  
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
 El tipo de elemento que expone la interfaz de enumerador.  
  
 `Copy`  
 Un homogéneos [copiar la clase de directiva](../../atl/atl-copy-policy-classes.md).  
  
 `ThreadModel`  
 El modelo de subprocesos de la clase. El valor predeterminado de este parámetro es el modelo de subprocesos del objeto global utilizado en el proyecto.  
  
## <a name="remarks"></a>Comentarios  
 `CComEnum`define un objeto de enumerador COM basado en una matriz. Esta clase es análoga a [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) que implementa un enumerador que se basa en un contenedor de la biblioteca estándar de C++. Los pasos típicos para utilizar esta clase se describen a continuación. Para obtener más información, consulte [colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class"></a>Para utilizar esta clase:  
  
- `typedef`una especialización de esta clase.  
  
-   Utilice la `typedef` como argumento de plantilla en la especialización de `CComObject`.  
  
-   Cree una instancia de la `CComObject` especialización.  
  
-   Inicializar el objeto de enumerador llamando a [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).  
  
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
 El código siguiente proporciona una función reutilizable para crear e inicializar un objeto de enumerador.  
  
 [!code-cpp[NVC_ATL_COM&#32;](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 Esta función de plantilla puede utilizarse para implementar la `_NewEnum` propiedad de una interfaz de colección, como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM Nº&33;](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 Este código crea un `typedef` de `CComEnum` que expone un vector de **VARIANT**s a través de la **IEnumVariant** interfaz. El **CVariantArrayCollection** clase simplemente especializa **CreateEnumerator** para trabajar con objetos del enumerador de este tipo y pasa los argumentos necesarios.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Clase CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)

