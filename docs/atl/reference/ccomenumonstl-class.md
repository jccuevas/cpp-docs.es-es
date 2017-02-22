---
title: "CComEnumOnSTL Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComEnumOnSTL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnumOnSTL class"
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComEnumOnSTL Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase define un objeto COM de enumerador basándose en una colección de STL.  
  
## Sintaxis  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class CollType,  
   class ThreadModel = CComObjectThreadModel  
>  
class ATL_NO_VTABLE CComEnumOnSTL :  
   public IEnumOnSTLImpl<Base, piid, T, Copy, CollType>,  
   public CComObjectRootEx< ThreadModel >  
```  
  
#### Parámetros  
 `Base`  
 Una interfaz COM de enumerador \(\).  
  
 `piid`  
 Un puntero al identificador de la interfaz de la interfaz del enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz del enumerador.  
  
 `Copy`  
 una clase de [directiva de copia](../../atl/atl-copy-policy-classes.md) .  
  
 `CollType`  
 Una clase de contenedor de STL.  
  
## Comentarios  
 `CComEnumOnSTL` define un objeto COM de enumerador basándose en una colección de STL.  Esta clase se puede usar en solitario o junto con [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  Los pasos típicos para utilizar esta clase se describen a continuación.  Para obtener más información, vea [Colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## para utilizar esta clase con ICollectionOnSTLImpl:  
  
-   `typedef` una especialización de esta clase.  
  
-   Utilice `typedef` como argumento final de plantilla en una especialización de `ICollectionOnSTLImpl`.  
  
 Vea [Colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md) para obtener un ejemplo.  
  
## para utilizar esta clase independientemente de ICollectionOnSTLImpl:  
  
-   `typedef` una especialización de esta clase.  
  
-   Utilice `typedef` como argumento de plantilla en una especialización de `CComObject`.  
  
-   Cree una instancia de especialización de `CComObject` .  
  
-   Inicializa el objeto enumerator llamando a [IEnumOnSTLImpl:: Iniciar](../Topic/IEnumOnSTLImpl::Init.md).  
  
-   Devuelve la interfaz del enumerador al cliente.  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Ejemplo  
 El código muestra siguiente proporciona una función genérica para controlar la creación y la inicialización de un objeto de enumerador:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/CPP/ccomenumonstl-class_1.h)]  
  
 Esta función de plantilla se puede utilizar para implementar la propiedad de `_NewEnum` de una interfaz de intercalación como se muestra a continuación:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/CPP/ccomenumonstl-class_2.h)]  
  
 Este código crea `typedef` para `CComEnumOnSTL` que expone un vector de s para `CComVariant`mediante la interfaz de **IEnumVariant** .  La clase de **CVariantCollection** especializada simplemente **CreateSTLEnumerator** para trabajar con objetos de enumeradores de este tipo.  
  
## Vea también  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Ejemplo ATLCollections: Muestra ICollectionOnSTLImpl, CComEnumOnSTL, y clases de directivas de copia personalizadas](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md)   
 [IEnumOnSTLImpl Class](../../atl/reference/ienumonstlimpl-class.md)